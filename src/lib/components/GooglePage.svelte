<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  
  let googlePage;
  
  function handleClick() {
    dispatch('interact');
  }
</script>

<div id="googlePage" bind:this={googlePage} on:click={handleClick}>
  <div class="header">
    <div class="logo">Markus<span>Search</span></div>
    <div class="nav-links">
      <button type="button" aria-label="Images search">Images</button>
      <button type="button" aria-label="Videos search">Videos</button>
      <button type="button" aria-label="News search">News</button>
      <button type="button" aria-label="More options">More</button>
    </div>
  </div>
  <div class="search-container">
    <input type="text" class="search-box" value="Faxe kondi beer pyramid" readonly>
    <div class="search-result">
      <div class="result-title">Faxe Kondi Beer Pyramid - The Ultimate Party Setup</div>
      <div class="result-url">
        <img src="https://www.google.com/favicon.ico" alt="icon">
        www.partyhacks.com › faxe-kondi-pyramid
      </div>
      <div class="result-description">Learn how to build the perfect Faxe Kondi beer pyramid for your next party. Step-by-step guide with measurements and tips for stability. Perfect for Markus-style gatherings.</div>
    </div>
    <div class="search-result">
      <div class="result-title">Se Giil på fylla - Markus' Epic Blog Post</div>
      <div class="result-url">
        <img src="https://www.google.com/favicon.ico" alt="icon">
        www.markusblog.com › se-giil-på-fylla
      </div>
      <div class="result-description">Read Markus' legendary blog post about the time he saw Giil while completely wasted. A story that has become part of local folklore and is still talked about to this day.</div>
    </div>
    <div class="search-result">
      <div class="result-title">Gir Moe en skarp høyre - YouTube</div>
      <div class="result-url">
        <img src="https://www.youtube.com/favicon.ico" alt="icon">
        www.youtube.com › watch
      </div>
      <div class="video-preview">
        <img src="https://i.ytimg.com/vi/8wV9J4tXgcM/maxresdefault.jpg" alt="video thumbnail">
        <div class="video-info">
          <div class="video-title">Gir Moe en skarp høyre - The Full Story</div>
          <div class="video-channel">Markus Channel • 1.2M views • 2 years ago</div>
        </div>
      </div>
    </div>
    <div class="search-result">
      <div class="result-title">Faxe Kondi vs. Other Beers - The Ultimate Taste Test</div>
      <div class="result-url">
        <img src="https://www.google.com/favicon.ico" alt="icon">
        www.beerreviews.com › faxe-kondi-comparison
      </div>
      <div class="result-description">A comprehensive comparison of Faxe Kondi against other popular beers. Includes Markus' personal rating system and recommendations for different occasions.</div>
    </div>
  </div>
</div>

<style>
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    border-bottom: 1px solid #e0e0e0;
  }

  .logo {
    font-size: 1.5rem;
    font-weight: bold;
  }

  .logo span {
    color: #4285f4;
  }

  .nav-links {
    display: flex;
    gap: 1rem;
  }

  .nav-links button {
    background: none;
    border: none;
    color: #5f6368;
    cursor: pointer;
    padding: 0.5rem;
    font-size: 0.9rem;
  }

  .nav-links button:hover {
    color: #1a73e8;
  }

  .search-container {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 1rem;
    width: 100%;
    box-sizing: border-box;
  }

  .search-box {
    width: 100%;
    padding: 1rem;
    border: 1px solid #dfe1e5;
    border-radius: 24px;
    font-size: 1rem;
    margin-bottom: 2rem;
    box-shadow: 0 1px 6px rgba(32, 33, 36, 0.28);
    box-sizing: border-box;
  }

  .search-result {
    margin-bottom: 2rem;
    padding: 1rem;
    border-radius: 8px;
    transition: background-color 0.2s;
  }

  .search-result:hover {
    background-color: #f8f9fa;
  }

  .result-title {
    color: #1a0dab;
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
    cursor: pointer;
  }

  .result-title:hover {
    text-decoration: underline;
  }

  .result-url {
    color: #202124;
    font-size: 0.9rem;
    margin-bottom: 0.5rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .result-url img {
    width: 16px;
    height: 16px;
  }

  .result-description {
    color: #4d5156;
    font-size: 0.9rem;
    line-height: 1.4;
  }

  .video-preview {
    display: flex;
    gap: 1rem;
    margin-top: 1rem;
    cursor: pointer;
  }

  .video-preview img {
    width: 120px;
    height: 90px;
    object-fit: cover;
    border-radius: 4px;
  }

  .video-info {
    flex: 1;
  }

  .video-title {
    color: #1a0dab;
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
  }

  .video-channel {
    color: #4d5156;
    font-size: 0.9rem;
  }

  @media (max-width: 768px) {
    .search-container {
      padding: 0 0.5rem;
      margin: 1rem auto;
    }

    .search-box {
      padding: 0.8rem;
      font-size: 0.9rem;
    }

    .result-title {
      font-size: 1.1rem;
    }

    .video-preview {
      flex-direction: column;
    }

    .video-preview img {
      width: 100%;
      height: auto;
      aspect-ratio: 16/9;
    }
  }
</style> 