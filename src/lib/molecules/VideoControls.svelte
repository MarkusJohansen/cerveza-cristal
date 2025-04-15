<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  
  export let player: any;
  
  onMount(() => {
    if (!browser) return;
    
    // Add error handling
    player.on('error', handleError);
    
    // Handle orientation changes
    window.addEventListener('orientationchange', handleOrientationChange);
    
    // Prevent default touch behaviors
    document.addEventListener('touchmove', handleTouchMove, { passive: false });
    
    return () => {
      player.off('error', handleError);
      window.removeEventListener('orientationchange', handleOrientationChange);
      document.removeEventListener('touchmove', handleTouchMove);
    };
  });
  
  function handleError() {
    console.error('Video error:', player.error());
    // Try to recover from error
    player.load();
  }
  
  function handleOrientationChange() {
    // Reload video on orientation change
    player.load();
  }
  
  function handleTouchMove(e: TouchEvent) {
    e.preventDefault();
  }
</script>

<style>
  :global(.video-js) {
    -webkit-tap-highlight-color: transparent;
    touch-action: manipulation;
  }
</style> 