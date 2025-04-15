<script lang="ts">
  export let value: string;
</script>

<div class="search-container">
  <input type="text" class="search-box" {value} readonly>
</div>

<style>
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

  @media (max-width: 768px) {
    .search-container {
      padding: 0 0.5rem;
      margin: 1rem auto;
    }

    .search-box {
      padding: 0.8rem;
      font-size: 0.9rem;
    }
  }
</style> 