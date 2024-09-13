---
layout: post
title: About
permalink: /about/
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-family: 'Product Sans', sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: white;
        }
        .container {
            width: 80%;
            margin: auto;
            overflow: hidden;
        }
        header {
            background: white;
            color: #333; /* Changed from #fff to #333 for better visibility */
            padding-top: 30px;
            min-height: 70px;
            border-bottom: #ddd 3px solid;
            text-align: center;
        }
        header h1 {
            margin: 0;
            font-size: 2.5em;
        }
        .accordion {
            background: black;
            color: #fff;
            cursor: pointer;
            padding: 15px;
            border: none;
            text-align: left;
            outline: none;
            font-size: 1.2em;
            width: 100%;
            border-radius: 8px;
            margin-bottom: 5px;
        }
        .accordion:hover {
            background: #555;
        }
        .flag {
          border-radius: none;
          margin: 40px;
          width: 150%; /* Or any size you need */
          height: auto; 
        }
        .panel {
            padding: 20px;
            background: #fff;
            display: none;
            overflow: hidden;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        .basic {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        h2, h3 {
            color: #333;
        }
        .slot {
            margin: 10px 0;
            padding: 10px;
            border: 1px dashed #ccc;
            border-radius: 8px;
            text-align: center;
            color: #888;
        }
        .gallery {
            display: block;
            white-space: nowrap;
            overflow-x: auto;
            padding: 10px 0;
        }
        .gallery img {
            display: inline-block;
            margin-right: 10px;
            max-height: 150px;
            border-radius: 8px;
            cursor: pointer;
        }
        .description {
            display: none;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 8px;
            background: #fff;
            margin-top: 10px;
        }
         .image-container {
            display: flex;
            flex-direction: column;
            width: 100%; /* Make the container width 100% of its parent */
           /* Center the images horizontally */
        }
        .image-container img {
            margin-right: 10px; /* Optional: Adds space between images */
            max-width: 40%; /* Ensures images fit within their container */
            height: auto; 
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <button class="accordion">About Me</button>
        <div class="panel">
            <p>My name is Vibha Ganji, and I'm currently in the 11th grade. Last year, I took the AP Computer Science Principles (CSP) course, which sparked my enthusiasm for technology and programming. This year, I'm excited to be taking AP Computer Science A (CSA) to deepen my skills in software development and algorithms.</p>
            <p>I have experience with several technologies, including JavaScript, HTML, SCSS, and SQLite databases.</p>
        </div>

        <button class="accordion">Location & Background</button>
<div class="panel">
    <p>
        I was born in Hyderabad, India and moved to San Diego when I was 5 years old.
        I attended Del Sur Elementary, Oak Valley Middle School, and I am currently a student at Del Norte High School.

        <div class = "image-container">

        <img src = "https://upload.wikimedia.org/wikipedia/en/thumb/4/41/Flag_of_India.svg/1200px-Flag_of_India.svg.png">

        <img src = "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a9/Flag_of_the_United_States_%28DoS_ECA_Color_Standard%29.svg/255px-Flag_of_the_United_States_%28DoS_ECA_Color_Standard%29.svg.png">

        </div>


    </p>
    <p>My parents are originally from India.</p>
</div>


        <button class="accordion">Hobbies</button>
        <div class="panel">
            <div class="gallery">
                <img class = "basic" src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Kuchipudi_Performer_DS.jpg/440px-Kuchipudi_Performer_DS.jpg" alt="Indian Classical Dance" data-description="Indian Classical Dance (Kuchipudi for 10 years)">
                <img src="https://m.media-amazon.com/images/I/81RBTG28sCL._AC_UF1000,1000_QL80_.jpg" alt="Reading" class = "basic" data-description="Reading (my favorite book of all time)">
                <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTAp7VYUXeqhIurQagTsZdYF_meZZfEE0aNtQ&s" alt="Travel" class = "basic" data-description="Travel (my favorite destination is Niagara Falls)">
            </div>
            <div id="image-description" class="description"></div>
        </div>

        <button class="accordion">Favorite Foods</button>
        <div class="panel">
            <div class="slot">
                <img src="https://carveyourcraving.com/wp-content/uploads/2021/06/chocolate-icecream-in-an-icecream-maker-500x500.jpg" alt="Ice Cream" class = "basic">
            </div>
            <div class="slot">
                <img src="https://sugargeekshow.com/wp-content/uploads/2019/01/triple-chocolate-cake-recipe.jpg" alt="Chocolate Cake" class = "basic">
            </div>
            <p>My favorite foods include:</p>
            <ul>
                <li><strong>Ice Cream:</strong> Ice Cream is one of my all-time favorite foods.</li>
                <li><strong>Chocolate Cake:</strong> Chocolate cake is my go-to dessert for a special treat.</li>
            </ul>
        </div>
    </div>
    <script>
        // Get all accordion buttons
        var acc = document.getElementsByClassName("accordion");
        var i;

        // Add event listeners to each accordion button
        for (i = 0; i < acc.length; i++) {
            acc[i].addEventListener("click", function() {
                // Toggle between adding and removing the "active" class
                // to highlight the button that controls the panel
                this.classList.toggle("active");

                // Toggle the panel's visibility
                var panel = this.nextElementSibling;
                if (panel.style.display === "block") {
                    panel.style.display = "none";
                } else {
                    panel.style.display = "block";
                }
            });
        }

        // Image click event handler to show descriptions
        var images = document.querySelectorAll('.gallery img');
        var descriptionBox = document.getElementById('image-description');

        images.forEach(function(image) {
            image.addEventListener('click', function() {
                descriptionBox.textContent = this.getAttribute('data-description');
                descriptionBox.style.display = 'block';
            });
        });
    </script>
</body>
</html>
