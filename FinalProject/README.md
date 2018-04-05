# Website Performance Optimization portfolio project

This is a Udacity project and the goal was to optimize the portfolios speed. The goal was that ```index.html``` is able to achieve at least a PageSpeed of 90 for Mobile and Desktop. My index.html was able to achieve 99 for Mobile and 96 for Desktop. I used this website to check the PageSpeed of ```index.html```: https://developers.google.com/speed/pagespeed/insights/.

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
I started off by looking at the ```changePizzaSizzes``` function. This is because this was the function that made an error occur when I resized the pizzas on the ```pizza.html``` page. What this does is it allows randomPizzaContainer to only be run once and not many times.

```  function changePizzaSizes(size) {
    var pizzaElements = document.querySelectorAll(".randomPizzaContainer");
    var dx = determineDx(pizzaElements[0.0], size);
    var newwidth = (pizzaElements[0.0].offsetWidth + dx) + 'px';
    for (var x = 0.0; x < pizzaElements.length; x++) {
      pizzaElements[x].style.width = newwidth;
    }
  }
```
Then, to improve the ```updatePositions``` function, this is what I did:
```  var items = document.querySelectorAll('.mover');
  var scrollY = document.documentElement.scrollY || document.scrollingElement.scrollTop;
  for (var i = 0; i < items.length; i++) {
    // document.body.scrollTop is no longer supported in Chrome.
    var phase = Math.sin((scrollY / 1250) + (i % 5));
    items[i].style.left = items[i].basicLeft + 100 * phase + 'px';
  }
  ```
  Here I just moved the var ```scrollY``` variable out of the function. I also changed two of the```scrollTop``` to ```scrollY``` which improved the pages scroll speed.
  I was able to figure this out on this website:https://stackoverflow.com/questions/20514596/document-documentelement-scrolltop-return-value-differs-in-chrome. I also changed "document.body.scrollTop" to ```document.scrollingElement.scrollTop``` because the old one wasn't supported in chrome anymore.

```document.addEventListener('DOMContentLoaded', function() {
  var cols = 8;
  var s = 256;
  var theMovingPizzas = document.getElementById("movingPizzas1");
  for (var i = 0; i < 40; i++) {
    var elem = document.createElement('img');
    elem.className = 'mover';
    elem.src = "images/pizza.png";
    elem.style.height = "100px";
    elem.style.width = "73.333px";
    elem.basicLeft = (i % cols) * s;
    elem.style.top = (Math.floor(i / cols) * s) + 'px';
    theMovingPizzas.appendChild(elem)
  }
  updatePositions();
});
```
I also moved this DOM call outside the for loop and saved it into a variable ```theMovingPizzas```. This is the reference that I used: https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById. Finally I also increased the number of sliding pizzas, in order to meet the specifications to 40.

### Final Comment
I shared my work with my sister Clara Krafft who is also right now working on this course. This is why we could have some similarities in our code.
