<slot />

<style>
  :global(body) {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background-color: #f8f9fa;
    color: #202124;
  }

  :global(header) {
    padding: 15px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #fff;
    border-bottom: 1px solid #dadce0;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  :global(logo) {
    font-size: 24px;
    font-weight: bold;
    color: #4285f4;
    display: flex;
    align-items: center;
  }

  :global(logo span) {
    color: #ea4335;
  }

  :global(nav-links) {
    display: flex;
    gap: 20px;
  }

  :global(nav-links a) {
    color: #5f6368;
    text-decoration: none;
    font-size: 14px;
    transition: color 0.2s ease;
  }

  :global(nav-links a:hover) {
    color: #1a0dab;
  }

  :global(search-container) {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    width: 100%;
    box-sizing: border-box;
  }

  :global(search-box) {
    width: 100%;
    padding: 15px 25px;
    border-radius: 24px;
    border: 1px solid #dfe1e5;
    font-size: 18px;
    margin: 20px 0;
    box-shadow: 0 1px 6px rgba(32, 33, 36, 0.28);
    background-color: #fff;
    transition: box-shadow 0.2s ease;
    box-sizing: border-box;
    -webkit-tap-highlight-color: transparent;
    touch-action: manipulation;
  }

  :global(search-box:focus) {
    outline: none;
    box-shadow: 0 1px 6px rgba(32, 33, 36, 0.28);
  }

  :global(search-result) {
    margin-bottom: 30px;
    padding: 20px;
    border-radius: 8px;
    cursor: pointer;
    background-color: #fff;
    border: 1px solid #dadce0;
    transition: all 0.3s ease;
    -webkit-tap-highlight-color: transparent;
    touch-action: manipulation;
  }

  :global(search-result:hover) {
    box-shadow: 0 2px 8px rgba(32, 33, 36, 0.1);
    transform: translateY(-2px);
  }

  :global(result-title) {
    color: #1a0dab;
    font-size: 24px;
    margin-bottom: 8px;
    font-weight: normal;
    transition: color 0.2s ease;
  }

  :global(search-result:hover .result-title) {
    color: #1557b0;
  }

  :global(result-url) {
    color: #202124;
    font-size: 16px;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
  }

  :global(result-url img) {
    width: 16px;
    height: 16px;
    margin-right: 8px;
  }

  :global(result-description) {
    color: #4d5156;
    font-size: 18px;
    line-height: 1.5;
  }

  :global(video-preview) {
    margin-top: 10px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  :global(video-preview img) {
    width: 120px;
    height: 68px;
    border-radius: 4px;
    object-fit: cover;
  }

  :global(video-info) {
    flex: 1;
  }

  :global(video-title) {
    font-size: 16px;
    color: #1a0dab;
    margin-bottom: 4px;
    transition: color 0.2s ease;
  }

  :global(search-result:hover .video-title) {
    color: #1557b0;
  }

  :global(video-channel) {
    font-size: 14px;
    color: #606060;
  }

  :global(video-js) {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: opacity 0.1s;
    z-index: 1000;
    -webkit-tap-highlight-color: transparent;
    touch-action: manipulation;
  }

  :global(video-js.visible) {
    opacity: 1;
  }

  @media (max-width: 768px) {
    :global(header) {
      flex-direction: column;
      align-items: flex-start;
      gap: 10px;
      padding: 10px 15px;
    }

    :global(nav-links) {
      width: 100%;
      justify-content: space-between;
    }

    :global(search-container) {
      padding: 10px 15px;
    }

    :global(search-box) {
      padding: 12px 20px;
      font-size: 16px;
      margin: 10px 0;
    }

    :global(result-title) {
      font-size: 20px;
    }

    :global(result-description) {
      font-size: 16px;
    }

    :global(video-preview) {
      flex-direction: column;
    }

    :global(video-preview img) {
      width: 100%;
      height: auto;
    }
  }

  @media (max-width: 480px) {
    :global(header) {
      padding: 8px 12px;
    }

    :global(search-container) {
      padding: 8px 12px;
    }

    :global(search-box) {
      padding: 10px 15px;
      font-size: 14px;
      margin: 8px 0;
    }

    :global(result-title) {
      font-size: 18px;
    }

    :global(result-description) {
      font-size: 14px;
    }

    :global(search-result) {
      padding: 15px;
      margin-bottom: 20px;
    }
  }
</style> 