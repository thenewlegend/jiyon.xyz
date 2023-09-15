<script>
  import { onMount, onDestroy } from 'svelte';

  let videoPlaying = true;

  onMount(() => {
    // Function to check if the video is playing
    function checkVideoPlaying() {
      videoPlaying = !video.paused && !video.ended;
    }

    // Get a reference to the video element
    const video = document.getElementById('top-video-phone');

    // Check if the video is playing when it's loaded
    video.addEventListener('loadeddata', checkVideoPlaying);

    // Check if the video is playing periodically
    const interval = setInterval(checkVideoPlaying, 1000);

    onDestroy(() => {
      // Clean up event listeners and intervals
      video.removeEventListener('loadeddata', checkVideoPlaying);
      clearInterval(interval);
    });
  });
</script>

<main>
  <div id="container">

  {#if videoPlaying}
    <!-- Display the video if it's playing -->
    <div id="video-container">
      <video id="top-video-phone" src="/bg.mp4" loop autoplay>
        <track kind="captions" src="" label="English Captions" default>
      </video>
    </div>
  {:else}
    <!-- Display an image if the video is not playing -->
    <div id="image-container">
      <img id="static" src="/static-pic.jpg" alt=" "/>
    </div>
  {/if}

  <div class="hi">
    <h1>Hi, I'm Jiyon</h1>
    <p>While this page is under construction, feel free to connect via LinkedIn</p>
    <p>Or send an email to <span id="email"><a href="mailto:jiyonpj2501@gmail.com" style="text-decoration: none; color:white" target="_blank">jiyonpj2501@gmail.com</a>
    </span></p>
    
    <div class="links">
      <a href="https://www.linkedin.com/in/jiyon/" target="_blank"><img class="linkedin" src="/linkedin.png" alt="LinkedIn"></a>
      <a href="https://github.com/thenewlegend" target="_blank"><img class="github" src="/github.png" alt="LinkedIn"></a>
      
    </div>

  </div>
</div>

</main>

<style>
  /* Your CSS styles for video, image, and other elements here */

  #container {
    display: flex;
    margin-top: 150px;
    justify-content: center;
    align-items: center;
    background-color: black;
  }

  video {
    object-fit: contain;
    width: 400px;
    filter: brightness(60%);
    opacity: 0.9;
    clip-path: ellipse(35% 50% at 50% 50%);
  }

  #static {
    object-fit: contain;
    width: 400px;
    filter: brightness(60%);
    opacity: 0.9;
    clip-path: ellipse(35% 50% at 50% 50%);
  }

  .hi {
    color: #ffffff;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-align: center;
    padding: 50px;
    margin: 0;
    font-size: 14px;
    text-shadow: 2px 2px 4px rgba(221, 194, 194, 0.1);
  }

  .links{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .linkedin {
    width: 40px;
    height: auto;
    filter: invert();
    transition: transform 0.3s ease-in-out;
  }

  .github{
    width: 60px;
    height: auto;
    filter: invert();
    transition: transform 0.3s ease-in-out;
  }

  .linkedin:hover, .github:hover {
  transform: scale(1.3);
}


   
#email {
  font-family: monospace; /* Use a monospaced font */
  font-size: 16px;
  color: #ffffff; /* Text color */
  display: inline-block; /* Make the span a block-level element for background animation */
  padding: 5px 0; /* Add some padding for better visual appearance */
  position: relative; /* Position relative for absolute positioning of pseudo-element */
}

/* Animation on hover */
#email::after {
  content: '🔒';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #000000; /* Grey background color */
  transition: width 0.3s ease-in-out; /* Smooth transition for width */
}

#email:hover::after {
  width: 0%; /* Expand the grey background from left to right on hover */
  cursor: pointer;
  content: '';
}


@media (max-width: 980px) {

  #container {
    display: flex;
    flex-direction: column;
    margin-top: 30px;
    justify-content: center;
    align-items: center;
    background-color: black;
  }

  .hi{
    margin-bottom: 20px;
    margin-top: 5px;
    padding-top: 0;
  }
  
  video {
    object-fit: contain;
    width: 300px;
    filter: brightness(60%);
    opacity: 0.9;
    clip-path: ellipse(35% 50% at 50% 50%);
  }

}

</style>
