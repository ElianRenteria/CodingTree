<script>
    import { onMount } from "svelte";
  
    let iframeLoaded = false;
  
    // Function to handle iframe load event with delay
    const handleIframeLoad = () => {
      setTimeout(() => {
        iframeLoaded = true; // Show iframe after 1 second delay
      }, 1100); // 1000ms = 1 second
    };
  </script>
  
  <div id="content">
    {#if !iframeLoaded}
      <!-- Show spinner while iframe is loading -->
      <span aria-busy="true" class="loading"></span>
    {/if}
  
    <!-- Iframe is initially hidden -->
    <iframe
      id="yourcode"
      title="code"
      src="https://trinket.io/embed/pygame"
      width="100%"
      height="100%"
      frameborder="0"
      marginwidth="0"
      marginheight="0"
      allowfullscreen
      on:load={handleIframeLoad}
      style="display: {iframeLoaded ? 'block' : 'none'};"
    ></iframe>
  </div>
  
  <style>
    #content {
      width: 100%;
      height: 90vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
  
    .loading {
      font-size: 3rem;
    }
  
    iframe {
      width: 100%;
      height: 100%;
    }
  </style>
  