<script lang="ts">
  // No props or state needed for this component
</script>

<div class="header">
  <div class="logo">Markus<span>Search</span></div>
  <div class="nav-links">
    <button type="button" aria-label="Images search">Images</button>
    <button type="button" aria-label="Videos search">Videos</button>
    <button type="button" aria-label="News search">News</button>
    <button type="button" aria-label="More options">More</button>
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
</style> 