<script>
  import { browser } from '$app/environment';
  import GooglePage from '$lib/components/GooglePage.svelte';
  import VideoPlayer from '$lib/components/VideoPlayer.svelte';
  
  let showVideo = false;
  
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
  {#if browser}
    <link href="/node_modules/video.js/dist/video-js.min.css" rel="stylesheet" />
  {/if}
</svelte:head>

{#if !showVideo}
  <GooglePage on:interact={handleInteraction} />
{/if}

<VideoPlayer visible={showVideo} />

<style>
  /* ... existing styles ... */
</style> 