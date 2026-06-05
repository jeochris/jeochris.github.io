---
layout: page
title: Misc
permalink: /misc/
nav: false
---

<style>
  .misc-section { margin-bottom: 3rem; }
  .poster-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
    gap: 12px;
  }
  .poster-grid img {
    width: 100%;
    aspect-ratio: 2 / 3;
    object-fit: cover;
    border-radius: 6px;
  }
  .album-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 12px;
  }
  .album-grid img {
    width: 100%;
    aspect-ratio: 1 / 1;
    object-fit: cover;
    border-radius: 6px;
  }
  .photo-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }
  .photo-grid img {
    width: 100%;
    aspect-ratio: 4 / 3;
    object-fit: cover;
    border-radius: 6px;
  }
  .sports-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 24px;
    align-items: center;
  }
  .sports-grid img {
    height: 120px;
    width: auto;
    object-fit: contain;
  }
  .placeholder-box {
    background-color: var(--global-divider-color);
    opacity: 0.3;
    border-radius: 6px;
  }
  .misc-section h2 {
    font-size: 1.3rem;
    margin-bottom: 0.5rem;
    margin-top: 0;
  }
  .misc-section p {
    color: var(--global-text-color);
    opacity: 0.6;
    font-size: 0.9rem;
    margin-bottom: 1rem;
  }
</style>

<div class="misc-section">
<h2>🎬 Movies</h2>
<p>Films I rated 5 stars</p>
<div class="poster-grid">
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 2/3;"></div>
</div>
</div>

---

<div class="misc-section">
<h2>📷 Photos</h2>
<p>Shots I've taken</p>
<div class="photo-grid">
  <div class="placeholder-box" style="aspect-ratio: 4/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 4/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 4/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 4/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 4/3;"></div>
  <div class="placeholder-box" style="aspect-ratio: 4/3;"></div>
</div>
</div>

---

<div class="misc-section">
<h2>🎵 Music</h2>
<p>Albums I've liked</p>
<div class="album-grid">
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
  <div class="placeholder-box" style="aspect-ratio: 1/1;"></div>
</div>
</div>

---

<div class="misc-section">
<h2>🏅 Sports</h2>
<p>Teams I support</p>
<div class="sports-grid">
  <img src="/assets/img/misc/sports/mancity.svg" alt="Manchester City">
  <img src="/assets/img/misc/sports/celtics.svg" alt="Boston Celtics">
  <div class="placeholder-box" style="height: 120px; width: 120px;"></div>
</div>
</div>
