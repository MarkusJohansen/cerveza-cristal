<script lang="ts">
  import { browser } from '$app/environment';
  import GooglePage from '$lib/molecules/GooglePage.svelte';
  import VideoPlayer from '$lib/molecules/VideoPlayer.svelte';
  
  // State
  let showVideo = false;
  
  // Effects
  if (browser) {
    import('video.js/dist/video-js.min.css');
  }
  
  // Event handlers
  function handleInteraction() {
    if (!browser) return;
    
    // Change favicon and title
    document.getElementById('pageFavicon').href = '/cerveza-cristal.png';
    document.title = 'Cerveza Cristalllll';
    
    // Show video immediately
    showVideo = true;
  }
</script>

<svelte:head>
  <title>Markus Search</title>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="black" />
  <link rel="icon" href="%sveltekit.assets%/favicon.ico" id="pageFavicon">
</svelte:head>

{#if !showVideo}
  <GooglePage on:interact={handleInteraction} />
{/if}

<VideoPlayer {showVideo} />

<style>
  /* ... existing styles ... */
</style> 