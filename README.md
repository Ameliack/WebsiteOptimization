# Website Performance Optimization portfolio project

This is a Udacity project and the goal was to optimize the portfolios speed. The goal was that ```index.html``` is able to achieve at least a PageSpeed of 90 for Mobile and Desktop. My index.html was able to achieve 99 for Mobile and 91 for Desktop. I used this website to check the PageSpeed of ```index.html```: https://developers.google.com/speed/pagespeed/insights/.

To run the code you can either download the folder onto your machine or navigate to this website: https://ameliack.github.io/WebsiteOptimization/FinalProject/index.html

## Installing this project
1. Visit this website: https://github.com/Ameliack/WebsiteOptimization. This is so that you can view my project on github.
2. Click on the *clone or download* button and then download it as a zip file.
3. Now open the ```index.html``` file on your computer or machine
4. Now you have it.

## Optimizations I made to ```index.html```
* I compressed the images so that they weren't so large. I used this website to do so: http://compressimage.toolur.com/.
* I used the ```async``` attribute for javascript.
* I inlined the css in ```index.html```
* I included ```media="print"``` for the print stylesheet.
* I also removed the google fonts style

## Optimizations I made to main.js (for ```pizza.html```)
I started off by looking at the ```changePizzaSizzes``` function. This is because this was the function that made an error occur when I resized the pizzas on the ```pizza.html``` page.

```  function changePizzaSizes(size) {
    var pizzaElements = document.querySelectorAll(".randomPizzaContainer");
    var dx = determineDx(pizzaElements[0.0], size);
    var newwidth = (pizzaElements[0.0].offsetWidth + dx) + 'px';
    for (var x = 0.0; x < pizzaElements.length; x++) {
      pizzaElements[x].style.width = newwidth;
    }
  }
```
Then, to improve the ```updatePositions``` function, all I had to do was change ```scrollTop``` to ```scrollY``` because that function was no longer supported in Chrome. After I did this optimization to the code, the page was able to scroll smoothly and under 1 millisecond.
