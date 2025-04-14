<script>
  import '../app.css';
</script>

<slot />

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
    background-color: #f8f9fa;
    color: #202124;
  }

  :global(.video-js) {
    position: fixed !important;
    top: 0 !important;
    left: 0 !important;
    width: 100% !important;
    height: 100% !important;
    object-fit: cover !important;
    opacity: 0;
    transition: opacity 1s ease-in;
    z-index: 1000;
    background-color: #000;
    -webkit-tap-highlight-color: transparent;
    display: block;
    visibility: hidden;
  }

  :global(.video-js.visible) {
    visibility: visible;
    opacity: 1;
  }

  :global(.hidden) {
    display: none;
  }
</style> 