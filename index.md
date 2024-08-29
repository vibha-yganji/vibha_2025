---
layout: base
title: Vibha Ganji's Home Page
description: Home Page
hide: true
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plane Over Ocean Animation</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            overflow: hidden;
            height: 100%;
        }
        #ocean {
            position: absolute;
            bottom: 0;
            width: 200%;
            height: 50%;
            background: linear-gradient(to top, #00008b, #00bfff);
        }
        #plane {
            position: absolute;
            top: 20%;
            left: -100px; /* Start off-screen */
            width: 100px;
            height: auto;
        }
    </style>
</head>
<body>
    <div id="ocean"></div>
    <img id="plane" src="plane.png" alt="Plane">

    <script>
        const plane = document.getElementById('plane');

        let planePos = -100; // Starting position of the plane
        const speed = 2; // Speed of the plane

        function animatePlane() {
            planePos += speed;
            plane.style.left = planePos + 'px';

            // If the plane goes off the right side of the screen, reset it
            if (planePos > window.innerWidth) {
                planePos = -100; // Reset to starting position
            }

            requestAnimationFrame(animatePlane);
        }

        // Start the animation
        animatePlane();
    </script>
</body>
</html>
