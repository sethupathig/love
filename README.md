<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For You</title>
    <style>
        :root {
            --bg-dark: #051a07;
            --glow-green: #a5d6a7;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body, html {
            height: 100%;
            width: 100%;
            overflow: hidden;
            background-color: var(--bg-dark);
            cursor: pointer;
        }

        .container {
            width: 100vw;
            height: 100vh;
            background: radial-gradient(circle at center, #143317 0%, var(--bg-dark) 100%);
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* The Panda Styling */
        .panda-wrapper {
            position: relative;
            width: 200px;
            animation: float 4s infinite ease-in-out;
        }

        /* Glowing light behind panda */
        .panda-wrapper::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 140px;
            height: 140px;
            background: rgba(165, 214, 167, 0.4);
            filter: blur(50px);
            z-index: 1;
        }

        .panda-img {
            width: 100%;
            position: relative;
            z-index: 2;
            display: block;
        }

        /* Floating animation for a soft feel */
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        #player { position: absolute; width: 0; height: 0; visibility: hidden; }
    </style>
</head>
<body onclick="startExperience()">

    <div id="player"></div>

    <div class="container">
        <div class="panda-wrapper">
            <img src="panda.png" alt="Panda" class="panda-img">
        </div>
    </div>

    <script>
        var tag = document.createElement('script');
        tag.src = "https://www.youtube.com/iframe_api";
        var firstScriptTag = document.getElementsByTagName('script')[0];
        firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

        var player;
        var hasStarted = false;

        function onYouTubeIframeAPIReady() {
            player = new YT.Player('player', {
                height: '0', width: '0',
                videoId: 'rtOvBOTyX00', 
                playerVars: { 'autoplay': 0, 'controls': 0, 'loop': 1 },
                events: { 'onReady': onPlayerReady }
            });
        }

        function onPlayerReady(event) {
            // Player is ready
        }

        function startExperience() {
            if (!hasStarted) {
                hasStarted = true;
                // Wait 2 seconds (2000 milliseconds) before playing
                setTimeout(function() {
                    if (player && player.playVideo) {
                        player.playVideo();
                    }
                }, 2000);
            }
        }
    </script>
</body>
</html>
