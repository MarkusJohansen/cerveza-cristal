<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  import Header from '../atoms/Header.svelte';
  import SearchBox from '../atoms/SearchBox.svelte';
  import SearchResult from '../molecules/SearchResult.svelte';
  
  // Event dispatcher
  const dispatch = createEventDispatcher();
  
  // Refs
  let googlePage: HTMLDivElement;
  
  // Event handlers
  function handleClick() {
    dispatch('interact');
  }

  function handleKeydown(event: KeyboardEvent) {
    if (event.key === 'Enter' || event.key === ' ') {
      event.preventDefault();
      dispatch('interact');
    }
  }
</script>

<div 
  id="googlePage" 
  bind:this={googlePage} 
  on:click={handleClick}
  on:keydown={handleKeydown}
  role="button"
  tabindex="0"
  aria-label="Click to reveal video"
>
  <Header />
  <div class="search-container">
    <SearchBox value="Faxe kondi beer pyramid" />
    <SearchResult
      title="Faxe Kondi Beer Pyramid - The Ultimate Party Setup"
      url="www.partyhacks.com › faxe-kondi-pyramid"
      description="Learn how to build the perfect Faxe Kondi beer pyramid for your next party. Step-by-step guide with measurements and tips for stability. Perfect for Markus-style gatherings."
      icon="https://www.google.com/favicon.ico"
    />
    <SearchResult
      title="Se Giil på fylla - Markus' Epic Blog Post"
      url="www.markusblog.com › se-giil-på-fylla"
      description="Read Markus' legendary blog post about the time he saw Giil while completely wasted. A story that has become part of local folklore and is still talked about to this day."
      icon="https://www.google.com/favicon.ico"
    />
    <SearchResult
      title="Gir Moe en skarp høyre - YouTube"
      url="www.youtube.com › watch"
      description=""
      icon="https://www.youtube.com/favicon.ico"
      isVideo={true}
      videoThumbnail="https://i.ytimg.com/vi/8wV9J4tXgcM/maxresdefault.jpg"
      videoTitle="Gir Moe en skarp høyre - The Full Story"
      videoChannel="Markus Channel • 1.2M views • 2 years ago"
    />
    <SearchResult
      title="Faxe Kondi vs. Other Beers - The Ultimate Taste Test"
      url="www.beerreviews.com › faxe-kondi-comparison"
      description="A comprehensive comparison of Faxe Kondi against other popular beers. Includes Markus' personal rating system and recommendations for different occasions."
      icon="https://www.google.com/favicon.ico"
    />
  </div>
</div>

<style>
  .search-container {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 1rem;
    width: 100%;
    box-sizing: border-box;
  }

  @media (max-width: 768px) {
    .search-container {
      padding: 0 0.5rem;
      margin: 1rem auto;
    }
  }
</style> 