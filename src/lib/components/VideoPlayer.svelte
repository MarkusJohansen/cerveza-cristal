<script>
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  
  let videoElement;
  let player;
  let videojs;
  let Hammer;
  let gsap;
  
  export let visible = false;
  
  onMount(async () => {
    if (browser) {
      videojs = (await import('video.js')).default;
      Hammer = (await import('hammerjs')).default;
      gsap = (await import('gsap')).gsap;

      if (videoElement) {
        player = videojs('cervezaVideo', {
          controls: false,
          autoplay: false,
          preload: 'auto',
          fluid: true,
          responsive: true,
          techOrder: ['html5'],
          html5: {
            vhs: {
              overrideNative: true
            },
            nativeTextTracks: false
          }
        });

        player.on('error', function() {
          console.log('Video error:', player.error());
          player.load();
          setTimeout(() => {
            player.play().catch(console.error);
          }, 100);
        });
      }

      // Handle orientation changes
      window.addEventListener('orientationchange', function() {
        player.load();
        if (visible) {
          player.play().catch(console.error);
        }
      });

      document.addEventListener('touchmove', function(e) {
        if (visible) {
          e.preventDefault();
        }
      }, { passive: false });
    }

    return () => {
      if (player) {
        player.dispose();
      }
    };
  });

  $: if (visible && player) {
    player.addClass('visible');
    gsap.to(player.el(), {
      opacity: 1,
      duration: 0.2
    });
    player.currentTime(30);
    const playPromise = player.play();
    
    if (playPromise !== undefined) {
      playPromise.then(() => {
        player.muted(false);
      }).catch(error => {
        console.log('Playback failed:', error);
        setTimeout(() => {
          player.play().then(() => {
            player.muted(false);
          }).catch(() => {
            setTimeout(() => {
              player.play().then(() => {
                player.muted(false);
              }).catch(console.error);
            }, 100);
          });
        }, 50);
      });
    }
  }
</script>

<video
  id="cervezaVideo"
  class="video-js vjs-default-skin vjs-big-play-centered"
  playsinline
  webkit-playsinline
  x5-playsinline
  x-webkit-airplay="allow"
  preload="auto"
  disablePictureInPicture
  controlsList="nodownload"
  muted
  bind:this={videoElement}
>
  <source src="/cerveza.mp4" type="video/mp4">
  Nettleseren din støtter ikke videoavspilling.
</video>

<style>
  :global(.video-js) {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: opacity 0.1s;
    z-index: 1000;
  }

  :global(.video-js.visible) {
    opacity: 1;
  }
</style> 