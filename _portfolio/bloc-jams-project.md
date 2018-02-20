---
layout: post
title: Bloc-Jams-Project
thumbnail-path: "bloc/bloc-jams/blocjams.png"
short-description: Bloc-Jams1 is a music player that allows you to sort within albums and navigate between songs easily.
---
# Summary
Bloc Jams1 is a gorgeously made platform that allows the User to easily navigate through albums and songs.
# Explanation
This project was my first, created with the Bloc program to assist in my learning of the facets of web development. My mentor, Carrie, was a great help to me in understanding the nuances of code and ways of simplifying it so it makes more sense and is more efficient.
# Problem
The user needs a web platform to play music on, we need to include several pages, graphics, and ingrained code behavior that changes based on circumstances. The problem lies in making all of this code work together, and not get tied up resulting in failure. There were issues during the entirety of the project, such as a page failing randomly due to a syntax error.
## Use Responsive Web Development
At this point, we've set up the bare bones of the project, but we still need to make sure it can be viewed on a plethora of media devices. The solution is to use responsive web development.
{% highlight javascript %}
<meta name="viewport" content="width=device-width, initial-scale=1">
{% endhighlight %}
This step sets the viewport, which is an HTML tag that indicates how the browser should render the content of the page in a device's viewport. It is a virtual window that contains the display of the browser's content. It belongs inside the head tag in index.html. We need this tag to properly render the HTML and CSS for each device.

Another vital step is to use a responsive grid to separate elements to collapse and expand based on device's breakpoints. The breakpoint corresponds to the width of a device's screen. We do this by using CSS media queries.
{% highlight javascript %}
/* Medium and small screens (640px)
 @media (min-width: 640px) {
   /* Style information will go here
 }
 /* Large screens (1024px)
 @media (min-width: 1024px) {
   /* Style information will go here
 }
{% endhighlight %}

## View albums and songs
Next, to view albums and songs, we need to see a collection of the available albums we can play. This means we must create a collection page for easy access. We link it on the collection.html page.
{% highlight javascript %}
<link rel="stylesheet" type="text/css" href="styles/collection.css">
{% endhighlight %}

Next, we want to consolidate the details on each album by adding sections. We create sections for the album cover image, the title, the artist, and release information.
{% highlight javascript%}
<main class="album-view container narrow">
             <section class="clearfix">
                 <div class="column half">
                     <img src="assets/images/album_covers/01.png" class="album-cover-art">
                 </div>
                 <div class="album-view-details column half">
                     <h2 class="album-view-title">The Colors</h2>
                     <h3 class="album-view-artist">Pablo Picasso</h3>
                     <h5 class="album-view-release-info">1909 Spanish Records</h5>
                 </div>
             </section>
{% endhighlight %}

Our next step is to add to the detail by creating a table for each song listing.There is a table row for each song, and we use placeholder data to create the skeleton.
{% highlight javascript %}
<table class="album-view-song-list">
                 <tr class="album-view-song-item">
                     <td class="song-item-number">1</td>
                     <td class="song-item-title">Blue</td>
                     <td class="song-item-duration">X:XX</td>
                 </tr>
{% endhighlight %}
## Animate Selling Points
Next, we use CSS transitions to animate between properties and change an element's appearance. We do this to animate the selling points on the landing page.
{% highlight javascript %}
.point {
     position: relative;
     padding: 2rem;
     text-align: center;
     opacity: 0;
     -webkit-transform: scaleX(0.9) translateY(3rem);
     -moz-transform: scaleX(0.9) translateY(3rem);
     transform: scaleX(0.9) translateY(3rem);
     -webkit-transition: all 0.25s ease-in-out;
     -moz-transition: all 0.25s ease-in-out;
     transition: all 0.25s ease-in-out;
     -webkit-transition-delay: 0.2s;
     -moz-transition-delay: 0.2s;
     transition-delay: 0.2s;
 }
{% endhighlight %}

To trigger the animations on the landing page, we need to write a JS program to activate the CSS transitions. We do this by adding a script tag at the end of the body tag.
{% highlight javascript %}
<script>
             // our JavaScript will go here
         </script>
     </body>
 </html>
{% endhighlight %}
## Write animatePoints function
Finally, we write a function named animatePoints. When called, this function will activate the CSS transition and update the styles we set in place in the CSS file. Our program alters the style of each point in the NodeList.
{% highlight javascript %}
var animatePoints = function() {

                var points = document.getElementsByClassName('point');

                var revealFirstPoint = function() {
                    points[0].style.opacity = 1;
                    points[0].style.transform = "scaleX(1) translateY(0)";
                    points[0].style.msTransform = "scaleX(1) translateY(0)";
                    points[0].style.WebkitTransform = "scaleX(1) translateY(0)";
                };

                var revealSecondPoint = function() {
                    points[1].style.opacity = 1;
                    points[1].style.transform = "scaleX(1) translateY(0)";
                    points[1].style.msTransform = "scaleX(1) translateY(0)";
                    points[1].style.WebkitTransform = "scaleX(1) translateY(0)";
                };

                var revealThirdPoint = function() {
                    points[2].style.opacity = 1;
                    points[2].style.transform = "scaleX(1) translateY(0)";
                    points[2].style.msTransform = "scaleX(1) translateY(0)";
                    points[2].style.WebkitTransform = "scaleX(1) translateY(0)";
                };

                revealFirstPoint();
                revealSecondPoint();
                revealThirdPoint();

            };
        </script>
{% endhighlight %}
Our next step is to link the javascript page to the index.html page.
{% highlight javascript %}
/section>
         <script src="scripts/landing.js"></script>
     </body>
 </html>
{% endhighlight %}
## Trigger Event Handler to execute on page load
The user is not going to trigger functions manually, so we must set up an event handler to trigger the function once the page has loaded.
{% highlight javascript %}
var animatePoints = function() {
    ...
};

window.onload = function() {
    alert("The window has loaded!");
}
{% endhighlight %}
## Remove Static for Dynamic
We need to set up our JavaScript file to generate album templates. This means we must remove the current static templates from collection.html.
We create a variable named collectionItemTemplate to hold the template. Now that we have a template assigned to a variable, we can use the variable to add as many albums as we want.
{% highlight javascript %}
window.onload = function() {

     var collectionContainer = document.getElementsByClassName('album-covers')[0];

     collectionContainer.innerHTML = '';


     for (var i = 0; i < 12; i++) {
         collectionContainer.innerHTML += collectionItemTemplate;
     }
 }
{% endhighlight %}
This causes the javascript to dynamically generate the album template. We assign this to a collectionContainer variable. We must clear the content before inserting content, and to do this, we assign an empty string to the collectionContainer's innerHTML property. We then create a for loop to add the contents of the template o the innerHTML of collectionContainer, and generates albums.

## Conclusion of problems
These were just some of the major issues I faced during the Bloc-Jams project. There were so many nuances and details during the process that make or break the ability to function.
# Solution
The problems were incredibly frustrating, but with the help of the Internet and my trusty mentor Carrie, I was able to research and find new ways to better understand syntax and how code will execute.
# Result
 The result of the research is expanded wisdom on how to solve problems and which resources to use. This is invaluable and will help me for the rest of my life. I would do things differently if I were to start this project over. I would keep all of my code extremely organized, be on top of every git commit I made, and write out pseudocode so I could really understand each line of code. I will use this knowledge in the future so I can feel less lost while programming.
