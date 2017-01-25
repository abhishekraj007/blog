---
layout: post
title: "How To Improve PageSpeed-A little Note"
image: ''
main-class: 'web'
color: '#4285f4'
tags:
    - web
    - performance
categories:
    - web
    - performance
twitter_text: 'How To Improve PageSpeed-A little Note'
---

Sometime you must have come across the moment when you fire up your browser to open new page and you're staring and waiting for the web page to load. You have got full signal even nothing is happening.

![](http://www.todayifoundout.com/wp-content/uploads/2011/12/site-problem.jpg)

The thing is you website owner have one second before a user starts to get distracted. JUST ONE SECOND.


So what causes a site to have slow load time? And how to you fix it?

(Page Insight)[] by Google is a very good tool which gives us an idea where you need to work to improve your page load time.

![](https://lh3.googleusercontent.com/eoWwThODhXOMqaDMdRVXKGS1b0hJ3ThGIajfFp2cGd2oGhIOwR4O5aWYubSX8S73YYafwXEn5NYrwLyaopFvtKU4JqEhqJs=s888)
Source: Google

There are many factors which contribute to page speed. But here I am going to talk about three tools which helps immensely in improving page load.

	1. Build Tools: Where you could minify the file and send less bytes down the wire, or merging multiple files, so rather than making four request, you only make one. 
	2. Page Structure: The second set of issue is on the structure of your page. For instance, where you link to your javascript files.
	3. Server side: This is place where you need little tweaks to enable things like caching of your page assets. 

###BUILD TOOLS:

There are a lot of build tools available on the web. Grunt and Gulp are one of them. These build tools are picking up a lot of steams in web dev community. And they are fairly easy to get grips with. I personally prefer using gulp.js in most my projects.

The main reason you'd want to use a build tool is to automate any set of tasks you're going to run on your project on a regular basis, like compling SASS files or compressing images. 

And most build tools will allow you to  pull in third party modules, which means you get a lot stuff for free.

Let's look at some of common file/modules by using which you can drastically decrease your file sizes, results in decreasing page loading time.

<strong>[gulp-uglify:](https://www.npmjs.com/package/gulp-uglify)</strong> This module takes your javascript files, strips out all white space, replaces variable names with shorter one, and then squishes all the file together. This way our javascript file is smaller making it faster to download, but  browser all have fewer file to download.

[gulp-cssmin](https://www.npmjs.com/package/gulp-css-minify) , [gulp-htmlmin:](https://www.npmjs.com/package/html-minifier) These packages uglify and compresses css and html files.

Another common problem area is image optimization.  When you run PageSpeed insights, it looks at your site, and checks whether any of the images are larger than they need to be, and in the guidelines it will recommend [jpegoptim](https://github.com/tjko/jpegoptim), a command line tool which strips out any metadata from the image files, and can lead to some really impressive reduction in file size.

To minimize images you can include following two module in your build task.

[gulp-imagemin:](https://www.npmjs.com/package/gulp-imagemin) For raster images.

[gulp-svgmin:](https://www.npmjs.com/package/gulp-svgmin) For vectors. This will strip out white space, and any unnecessary tags and attribute from your svg files.


###PAGE STRUCTURE:

In the initial stage of my learning web development. I always used to put all of my javascript files in the head of my page. 

```html

<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
        
        <script src="script.js"></script>
    </head>
<body>
    ----
    ----
</body>
</html>


```

I was completely unaware about the problem it causes. The problem with is that the browser will start to pass the documents, and as it reads the HTML tag, the HEAD tag, and it will eventually reach to your script tag, and this is where you'll see the page of bad times. Page stuck. 

The reason the page stops rendering is because JavaScript can manipulate the DOM and CSS. So the browser need to go and fetch the JavaScript from the server and execute it once it's downloaded. 

It's only the JavaScript is finished executing that the page can continue rendering.

So to avoid this delay, always put your javascript files at the bottom of body element.

```html

<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    
    </head>
<body>
    ----
    ----
    <script src="script.js"></script>
</body>
</html>


```

This way the browser can pass rendering the page up to this point, and then it'll handle fetching the JavaScript file at the very end. 

The second part of page structure is CSS link tag. When we add a CSS link tag, the rendering of the page  will block much like it did with JavaScript.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    
        <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" />
    </head>
<body>
    ----
    ----
    
</body>
</html>

```

If you're relying on some external CSS library to style your web page it causes the same problem just JavaScript does. Until browser completely download the CSS file user would see unstyled content. 

So avoid relying on CDN links for styling most important part of page. If possible put inline CSS in tag directly into the HTML. And then request rest CSS. 

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    
        
        <style>
        body {background-color: lightblue;font-family: verdana; font-size: 20px;} h1 {color: white; text-align: center;}
        </style>
    </head>
<body>
    ----
    ----
    
</body>
</html>


```


SERVER SIDE:

When the browser makes a request for a file from your server, it should always return a cache control max age header.  This is what tells the browser to cache a fie for how long, meaning the next time a user visits your page and it needs a file, it doesn't need to download it again. It's just good to go from the cache. 
 
When it comes to caching there are a few things you need to ask from yourself.

First, how long can I cache my files for?

Second, how do I actually get my server to return this cache control max age header?

And third, what do I do when I need to change a file?

Answering the first question of how long do I cache my files for, I personally found HTML5 Boilerplate to be a good source of guidance. 

```
.htaccess

# ----------------------------------------------------------------------
# | Expires headers                                                    |
# ----------------------------------------------------------------------

  # CSS

    ExpiresByType text/css                              "access plus 1 year"


  # Data interchange

    ExpiresByType application/atom+xml                  "access plus 1 hour"
    ExpiresByType application/rdf+xml                   "access plus 1 hour"
    ExpiresByType application/rss+xml                   "access plus 1 hour"

    ExpiresByType application/json                      "access plus 0 seconds"
    ExpiresByType application/ld+json                   "access plus 0 seconds"
    ExpiresByType application/schema+json               "access plus 0 seconds"
    ExpiresByType application/vnd.geo+json              "access plus 0 seconds"
    ExpiresByType application/xml                       "access plus 0 seconds"
    ExpiresByType text/xml                              "access plus 0 seconds"


  # Favicon (cannot be renamed!) and cursor images

    ExpiresByType image/vnd.microsoft.icon              "access plus 1 week"
    ExpiresByType image/x-icon                          "access plus 1 week"

  # HTML

    ExpiresByType text/html                             "access plus 0 seconds"


  # JavaScript

    ExpiresByType application/javascript                "access plus 1 year"
    ExpiresByType application/x-javascript              "access plus 1 year"
    ExpiresByType text/javascript                       "access plus 1 year"


  # Manifest files

    ExpiresByType application/manifest+json             "access plus 1 week"
    ExpiresByType application/x-web-app-manifest+json   "access plus 0 seconds"
    ExpiresByType text/cache-manifest                   "access plus 0 seconds"


  # Media files

    ExpiresByType audio/ogg                             "access plus 1 month"
    ExpiresByType image/bmp                             "access plus 1 month"
    ExpiresByType image/gif                             "access plus 1 month"
    ExpiresByType image/jpeg                            "access plus 1 month"
    ExpiresByType image/png                             "access plus 1 month"
    ExpiresByType image/svg+xml                         "access plus 1 month"
   

```


If you look at HTML5 Boilerplate's HD access file, there are number of caching rule defining the caching period depending on the type of file. These are general but you should define the time period accourding to your need. 

The answer to second and third question, what do I do when I need to change a file.

There is a very nice package, [gulp-rev](https://www.npmjs.com/package/gulp-rev), that you can include in your package to take care of revision. And and for server side take a look at [Gziip](https://www.gnu.org/software/gzip/)

