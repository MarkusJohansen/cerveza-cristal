<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  import VideoControls from './VideoControls.svelte';
  import { gsap } from 'gsap';
  
  // Props
  export let showVideo = false;
  
  // Refs
  let videoElement: HTMLVideoElement;
  
  // State
  let player: ReturnType<typeof import('video.js').default> | undefined;
  let videojs: typeof import('video.js').default;
  let Hammer: any;
  
  // Effects
  onMount(() => {
    const init = async () => {
      if (browser) {
        videojs = (await import('video.js')).default;
        Hammer = (await import('hammerjs')).default;

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

          if (player) {
            const currentPlayer = player;
            currentPlayer.on('error', function() {
              console.log('Video error:', currentPlayer.error());
              currentPlayer.load();
              setTimeout(() => {
                currentPlayer.play()!.catch(console.error);
              }, 100);
            });
          }
        }

        // Handle orientation changes
        window.addEventListener('orientationchange', function() {
          if (player) {
            const currentPlayer = player;
            currentPlayer.load();
            if (showVideo) {
              currentPlayer.play()!.catch(console.error);
            }
          }
        });

        document.addEventListener('touchmove', function(e) {
          if (showVideo) {
            e.preventDefault();
          }
        }, { passive: false });
      }
    };

    init();

    return () => {
      if (player) {
        player.dispose();
      }
    };
  });

  // Reactive statements
  $: if (showVideo && player) {
    const currentPlayer = player;
    currentPlayer.addClass('visible');
    gsap.to(currentPlayer.el(), {
      opacity: 1,
      duration: 0.1
    });
    currentPlayer.currentTime(30);
    const playPromise = currentPlayer.play();
    
    if (playPromise !== undefined) {
      playPromise.then(() => {
        currentPlayer.muted(false);
      }).catch((error: Error) => {
        console.log('Playback failed:', error);
        setTimeout(() => {
          currentPlayer.play()!.then(() => {
            currentPlayer.muted(false);
          }).catch(() => {
            setTimeout(() => {
              currentPlayer.play()!.then(() => {
                currentPlayer.muted(false);
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
  preload="auto"
  disablePictureInPicture
  controlsList="nodownload"
  muted
  bind:this={videoElement}
>
  <source src={encodeURI('/cerveza.mp4')} type="video/mp4">
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