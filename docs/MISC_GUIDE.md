# Misc 페이지 콘텐츠 추가 가이드

## 앨범 커버

### 파일 위치
`assets/img/misc/albums/<slug>.jpg`

### 추천 소스: MusicBrainz + Cover Art Archive

iTunes Search API는 아래 이유로 신뢰하기 어렵다:
- 동명 아티스트/앨범을 잘못 반환하는 경우 다수
- 싱글을 정규 앨범 대신 반환
- 욕설 포함 앨범명 필터링 (예: Norman Fucking Rockwell)
- 연속 요청 시 429 rate limit
- 한국 아티스트/음반 검색 결과 부정확

**MusicBrainz + Cover Art Archive를 기본으로 사용한다.**

#### 검색 순서

1. **MusicBrainz로 MBID 조회**
```python
import urllib.request, urllib.parse, json

headers = {'User-Agent': 'jeochris-site/1.0 (chris990126@gmail.com)'}
params = urllib.parse.urlencode({'query': 'artist name + album title', 'fmt': 'json', 'limit': '5'})
url = f"https://musicbrainz.org/ws/2/release-group/?{params}"
req = urllib.request.Request(url, headers=headers)
with urllib.request.urlopen(req) as r:
    data = json.loads(r.read())
for rg in data['release-groups']:
    print(rg['id'], rg['artist-credit'][0]['artist']['name'], rg['title'])
```

2. **Cover Art Archive로 이미지 다운로드**
```python
mbid = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
url = f"https://coverartarchive.org/release-group/{mbid}/front"
req = urllib.request.Request(url, headers=headers)
with urllib.request.urlopen(req) as r:
    data = r.read()
with open("assets/img/misc/albums/album-name.jpg", 'wb') as f:
    f.write(data)
```

3. **반드시 이미지를 직접 눈으로 확인한다** (Read 도구로 뷰)

#### 커버에 흰 테두리가 있을 때

Cover Art Archive에 같은 릴리즈의 이미지가 여러 개일 수 있다. 특정 릴리즈 ID로 전체 목록을 조회한다:
```python
# release-group MBID로 releases 목록 조회
url = f"https://musicbrainz.org/ws/2/release-group/{mbid}?inc=releases&fmt=json"
# → release ID 획득 후:
url = f"https://coverartarchive.org/release/{release_id}"
# → images[] 배열에서 front:true 아닌 것 중 더 나은 커버 선택
```

#### iTunes를 써야 할 때

검색이 안 될 때 Apple Music 웹에서 앨범 ID를 직접 찾아 lookup 사용:
```python
url = f"https://itunes.apple.com/lookup?id={album_id}"
# artworkUrl100 필드를 1200x1200 크기로 변환:
art_url = item['artworkUrl100'].replace('100x100bb', '1200x1200bb')
```

---

## 사진

### 파일 위치
`assets/img/misc/photos/<filename>.jpg`

### 압축 필수

원본을 그대로 넣으면 페이지 로딩이 매우 느려진다. **반드시 sips로 압축 후 업로드한다.**

```bash
# 단일 파일
sips --resampleWidth 1200 --setProperty formatOptions 70 input.jpg --out output.jpg

# 폴더 전체 일괄 처리
for f in ~/Desktop/photos/*.jpg; do
  sips --resampleWidth 1200 --setProperty formatOptions 70 "$f" \
    --out "assets/img/misc/photos/$(basename $f)"
done
```

- `resampleWidth 1200`: 가로 1200px로 리샘플 (세로는 비율 유지)
- `formatOptions 70`: JPEG 품질 70 (288MB → 13MB 수준으로 감소)
- PNG는 `--setProperty format jpeg` 옵션 추가

---

## 스포츠 로고

### 파일 위치
`assets/img/misc/sports/<team>.svg`

SVG 형식 권장. 모바일에서 `width: 100%; height: auto` CSS가 적용되어 있으므로 뷰박스가 올바르게 설정된 SVG를 사용한다.

---

## misc.md 섹션 구조

```html
<div class="misc-section" id="section-id">
<h2>Section Title</h2>
<div class="grid-class">
  <img src="/assets/img/misc/subdir/file.jpg" alt="...">
</div>
</div>
```

- `scroll-margin-top: 70px`이 `.misc-section`에 적용되어 있어 navbar 아래로 앵커 점프된다
- 홈 bio의 링크(`/misc/#movies` 등)와 id가 일치해야 한다
