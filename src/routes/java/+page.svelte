<script>
    import { onMount } from "svelte";
  
    let iframeLoaded = false;
  
    // Function to handle iframe load event with delay
    const handleIframeLoad = () => {
      setTimeout(() => {
        iframeLoaded = true; // Show iframe after 1 second delay
        const iframe = document.querySelector('#yourcode');
iframe.addEventListener('load', () => {
  const iframeDoc = iframe.contentDocument || iframe.contentWindow.document;

  // Now you can target the textarea inside the iframe (or any other element)
  const textArea = iframeDoc.querySelector('.ace_content');

  if (textArea) {
    textArea.textContent = 'Your new content here!';
  } else {
    console.error('Textarea not found inside the iframe.');
  }
});

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
      src="https://trinket.io/embed/java"
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
  