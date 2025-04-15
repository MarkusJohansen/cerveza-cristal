<script lang="ts">
  interface SearchResultProps {
    title: string;
    url: string;
    description: string;
    icon: string;
    isVideo?: boolean;
    videoThumbnail?: string;
    videoTitle?: string;
    videoChannel?: string;
  }

  export let title: string;
  export let url: string;
  export let description: string;
  export let icon: string;
  export let isVideo = false;
  export let videoThumbnail = '';
  export let videoTitle = '';
  export let videoChannel = '';
</script>

<div class="search-result">
  <div class="result-title">{title}</div>
  <div class="result-url">
    <img src={icon} alt="icon">
    {url}
  </div>
  <div class="result-description">{description}</div>
  {#if isVideo && videoThumbnail && videoTitle && videoChannel}
    <div class="video-preview">
      <img src={videoThumbnail} alt="video thumbnail">
      <div class="video-info">
        <div class="video-title">{videoTitle}</div>
        <div class="video-channel">{videoChannel}</div>
      </div>
    </div>
  {/if}
</div>

<style>
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