<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Short Videos</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: #000;
      color: #fff;
      font-family: sans-serif;
      overflow-x: hidden;
    }
    .video-container {
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      scroll-snap-align: start;
    }
    video {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .videos {
      height: 100vh;
      overflow-y: scroll;
      scroll-snap-type: y mandatory;
    }
  </style>
</head>
<body>
  <div class="videos">
    <div class="video-container">
      <video src="video1.mp4" autoplay muted loop playsinline></video>
    </div>
    <div class="video-container">
      <video src="video2.mp4" autoplay muted loop playsinline></video>
    </div>
    <div class="video-container">
      <video src="video3.mp4" autoplay muted loop playsinline></video>
    </div>
  </div>

  <script>
    const videos = document.querySelectorAll("video");

    function handlePlay() {
      videos.forEach(video => {
        const rect = video.getBoundingClientRect();
        if (rect.top >= 0 && rect.bottom <= window.innerHeight) {
          video.play();
        } else {
          video.pause();
        }
      });
    }

    document.querySelector(".videos").addEventListener("scroll", handlePlay);
    window.addEventListener("load", handlePlay);
  </script>
</body>
</html>
