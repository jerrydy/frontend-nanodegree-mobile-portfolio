## This is Jerry's Website Performance Optimization Portfolio Project

### index.html optimized for PageSpeed Insights
The index.html has been optimized to have a score of 93/100 for Mobile and 94/100 for Desktop. You can test this by running the following url http://jerrydy.github.io/mobile-portfolio in PageSpeed Insights. You may also clone this repository to your own computer and run your own web server using SimpleHTTPServer and exposing it to PageSpeed Insights using ngrok.

### Scrolling Pizza Optimized to run 60fps
Cam's Pizzaria page has been optimized so that the animation during scrolling is at least 60 fps.

### Resize Pizza Optimized to 1ms
And lastly, the pizza resizing has been optimized so each resize only takes about 1ms.

### Using the Build Tools

The package.json and Gruntfile.js files are also provided so grunt can be used to minify the css and js files used by index.html.

Make sure that npm and the grunt-cli is installed. Then use npm install to install grunt, grunt-contrib-cssmin and grunt-contrib-uglify. Then simply run grunt to automatically minify the css and js files.

### Optimizations in main.js

The best way to see the optimizations performed is to load main.js into an editor and search for 'jerryopt'. The optimizations performed are heavily documented in the source file. The following is a quick summary:

1. Line 455: Resizing the pizza was optimized by changing the width property of the randomPizzaContainer class instead of iterating through all the random pizzas one by one. This causes the browser to Recalculate Layout only once, instead of once for each random pizza.
2. Line 522: The phase offsets are precalculated before the loop starts, instead of repeatedly calculating it inside the loop.
3. Line 534: We put each pizza image in its own z-layer so only the pizza that got moved is repainted instead of the whole screen. We also use the translateX property to move the pizza image instead of left which caused the browser to skip the layout step.
4. Line 555: We calculate the number of moving pizzas needed for the screen size instead of hard-coding to use 200 pizzas, dramatically reducing the number of moving pizzas we need to draw.