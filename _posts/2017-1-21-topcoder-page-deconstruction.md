---
layout: post
title: "Topcoder Page Deconstruction-Analysis and replication"
image: 'images'
main-class: 'misc'
color: '#7aab13'
tags:
    - web
    - analysis
    - front-end
categories:
    - misc
    - web
    - analysis
    - front-end
---


Let's see the code and approach involved to replicate the similar design that you see on the front page of Topcoder website:

[Demo](https://abhishekraj007.github.io/apps/topcoder)

## Table of contents    
   
* [Navigation Menu](#navigation)
* [Section 1- Crowdsourcing1](#section1)
* [Section 2- Crowdsourcing2](#section2)  
* [Section 3- Community](#section3)  
* [Section 4- Challenge](#section4)
* [One page scrolling effect](#onepage)
* [Resources](#resources)
* [Note](#note)

<a name="navigation">
## Top Navigation Menu
First thing first, Build Top menu (Using bootstrap to make life little easy). 
Top header includes a logo at left side and two buttons at right side. The following html code will give required skeleton.

```html
<!--  Top Navigation Bar -->
    <header>
        <nav class="navbar navbar-default navbar-fixed-top">
            <div class="container-fluid">
                <div class="navbar-header">
                    <!-- Menu Button for small devices -->
                    <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#nav-menu" aria-expanded="false">
                        <span class="sr-only">Navigation</span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                      </button>
                      <!-- Logo -->
                    <a class="navbar-brand" href="#">top<strong>coder</strong></a>
                </div>
                <!-- navbar-header -->
                <!-- Links in right side-->
                <div class="collapse navbar-collapse" id="nav-menu">
                    <ul class="nav navbar-nav navbar-right">
                        <a href="#" class="btn btn-default">Contact Us</a>
                        <a href="#" class="btn btn-default">Log in</a>
                    </ul>
                </div> <!-- /.navbar-collapse -->
            </div>  <!-- /.container-fluid -->
        </nav> <!-- Nav -->
    </header><!-- header -->
    
```
(Read bootstrap documentation here, how to create a [navigation bar](http://getbootstrap.com/components/#navbar))

After writing above markup our navigation bar will look like this:
![nav1](https://raw.githubusercontent.com/abhishekraj007/topcoder-frontend/master/screenshots/nav1.PNG?raw=true)

CSS code to make our navigation bar look similar to topcoder navigation. (Note: You'll need a sass compiler to compile these scss code/ grab the compiled css code from the final source code)

```css
.navbar-default {
    background-color: $white;
    height: 80px;
    border-top: 1px solid $main;
    .container-fluid {
        margin-top: 15px;
        width: 95%;
        .navbar-right {
            padding: 6px;
            a {
                margin-left: 1em;
                text-transform: uppercase;
            }
        }
    }
}
// Making default-button style global so that it could be use anywhere on the page
.btn-default {
    background-color: $main;
    border-color: $main;
    color: $white;
    border-radius: 2px;
    font-size: 1.2em;
    padding-left: 1.2em;
    padding-right: 1.2em;
    font-weight: 600;
    text-transform: uppercase;
    &:hover {
        background-color: $blue-dark;
        border-color: $blue-dark;
        color: $white;
    }
    &:focus {
        background-color: $blue-dark;
        border-color: $blue-dark;
        color: $white;
    }
   
}

```
Now our final navigation will look something like this:

![styled navigation bar](https://github.com/abhishekraj007/topcoder-frontend/blob/master/screenshots/nav2.PNG?raw=true)



<a name="section1">
## Section 1- Crowdsourcing1

The first section is easy, It contain a `heading`, a `subheading` and below it, two `buttons` all floating to the left. paste the following html code to generate the required skeleton. 

```html
    <section>
            <div class="crowd-sourcing1">
                <div class="container">
                    <div class="row">
                        <div class="col-md-7 col-xs-12">
                            <h1>Deliver faster for your business through crowdsourcing.</h1>
                            <p>With a community of over 1,000,000 design and technology experts, Topcoder provides on-demand capability, bandwidth, and velocity so you can do more.</p>
                            <div class="two-buttons">
                                <a href="#">I want to get work done</a>
                                <a href="#">I want to join Topcoder</a>
                            </div><!-- two button -->
                        </div><!-- col -->
                    </div><!-- row -->
                </div><!-- container -->
            </div><!-- crowd-sourcing1 -->
        </section><!-- section -->

```
After writing above html markup, our code will generate view something like this:

![section1_1](https://github.com/abhishekraj007/topcoder-frontend/blob/master/screenshots/sec1_1.PNG?raw=true)

Now paste the following CSS code to match style with the first section of topcoder page:

```css
.crowd-sourcing1 {
    background: url('https://wwwtc.wpengine.com/wp-content/themes/tc2-theme/appirio-50-50/i/desktop/bg-deliver-crowdsourcing.jpg');
    background-size: cover;
    color: $white;
    height: 100%;
    width: 100%;
    padding-top: 50px;
    h1 {
        padding: 2em 0 0 0;
        font-size: 2.8em;
        line-height: 1.5em;
        letter-spacing: 1px;
    }
    p {
        padding: 1em 0 1em 0;
        font-size: 1.4em;
        letter-spacing: 1px;
    }
    .two-buttons {
        padding: 3em 0;
        margin-bottom: 3em;
        display: inline-block;
        a {
            border: 1px solid $white;
            border-radius: 2px;
            color: $white;
            text-decoration: none;
            font-size: 1.2em;
            padding: 1em 3em;
            margin: 1em 2em 0 0;
            display: inline-block;
            &:hover {
                background: rgba(246, 246, 246, 0.2);
                ;
            }
        }
    }
}

```

The output after pasting above css code will generate view something like this:

![section1_2](https://github.com/abhishekraj007/topcoder-frontend/blob/master/screenshots/sec1_2.PNG?raw=true)

<a name="section2">
## Section 2 - Crowdsourcing2

Now let's move to the section 2. This section contains one `heading` at the top and one `row` with 3 `columns`. Each column contains one big `icon`, `subheader` below the icon, a `paragraph`, and a `button` below the paragraph. To generate this type of skeleton paste the following html code in your editor.

```html
    <section>
            <div class="crowd-sourcing2">
                <div class="container text-center">
                    <div class="">
                        <h1>Crowdsourcing with Topcoder is exceptional for:</h1>
                    </div>
                    <div class="row">
                        <div class="col-md-4 design">
                            <div class="blue">
                                <i class="ion-ios-color-filter-outline"></i>
                                <h3>Design & Rapid Prototyping</h3>
                            </div>
                            <!-- blue -->

                            <p>Bring your app to life and uncover new possibilities with UX design and rapid prototyping. Get multiple ideas and options, quickly set the direction of your app, and accelerate progress to final products.</p>
                            <a class="btn btn-default" href="#">Learn More</a>
                        </div> <!-- col -->
                        <div class="col-md-4 app">
                            <div class="green">
                                <i class="ion-social-nodejs"></i>
                                <h3>Application Development</h3>
                            </div>
                            <p>You need exceptional development talent with breadth and depth in the latest technologies. Build apps that people love. Create, migrate, integrate. Build and release faster.</p>
                            <a class="btn btn-default" href="#">Learn More</a>
                        </div> <!-- col -->
                        <div class="col-md-4 algo">
                            <div class="orange">
                                <i class="ion-ios-analytics-outline"></i>
                                <h3>Alogorithm & Analytics</h3>
                            </div>
                            <p>Whether you need to optimize, analyze, or assess, using the power of the crowd accelerates and increases the creative thinking and real solutions that go into the ever-changing and rapidly growing world of data science.</p>
                            <a class="btn btn-default" href="#">Learn More</a>
                        </div><!-- col -->
                    </div> <!-- row -->
                </div> <!-- container -->
            </div> <!-- crowd-sourcing2 -->
        </section> <!-- section -->
```
Now to style this section to match with topcoder section 2 page, paste the following css code:

```css
.crowd-sourcing2 {
    color: $brown-text;
    width: 100%;
    height: 100%;
    padding-top: 50px;
    h1 {
        padding: 1em 0 0 0;
        font-size: 2.8em;
        line-height: 1.5em;
    }
    .row {
        width: 80%;
        margin: 1em auto 5em auto;
        i {
            font-size: 6em;
        }
        h3 {
            font-size: 1.8em;
            margin: 0;
        }
        p {
            font-size: 18px;
            padding: 5px 0 20px 0;
            margin: 6px auto;
        }
        a {
            text-transform: uppercase;
        }
    }
}

```

The final output of section 2 will look like this:

![section2](https://github.com/abhishekraj007/topcoder-frontend/blob/master/screenshots/sec2_1.PNG?raw=true)

<a name="section3">
## Section 3 - Community section

Now let's move to the section 3 of this page, this section comprises of one heading, one `paragraph` below the heading, one `row` with `three columns`, each columns consists of a big `h1` of different `colors` and below h1 a little `discription` in `uppercase`. Outside and below the row, there is a `button`.

The following html code will generate the required skeleton.

```html
    <section>
            <div class="community">
                <div class="container text-center">
                    <div class="row">
                        <div class="col-md-2">
                        </div>
                        <div class="col-md-8">
                            <h1>Meet Our Community</h1>
                            <p>
                                Topcoder is the world’s largest community of competitive designers, developers, and data scientists. Born in 2001, our community is represented in nearly every country across the globe. Topcoder is repeatable, on-demand crowdsourcing, done right, at massive
                                scale.
                            </p>
                            <div class="col-md-4 border-right">
                                <h1 class="large-text orange">1M</h1>
                                <span>Members</span>
                            </div>
                            <div class="col-md-4 border-right">
                                <h1 class="large-text green">7K+</h1>
                                <span>Crowdsourcing challenge per year</span>
                            </div>
                            <div class="col-md-4">
                                <h1 class="large-text blue">$80M</h1>
                                <span>Paid to our community</span>
                            </div>

                        </div>
                        <div class="col-md-2"></div>
                    </div> <!--row -->
                    <a class="btn btn-default" href="#">Explore out community</a>
                </div><!-- container -->
            </div><!-- community -->
        </section>
```
To style the above skeleton use following css code (note: some of the classes I have mentioned are global and will see later in final code)

```css
.crowd-sourcing2 {
    color: $brown-text;
    width: 100%;
    height: 100%;
    padding-top: 50px;
    h1 {
        padding: 1em 0 0 0;
        font-size: 2.8em;
        line-height: 1.5em;
    }
    .row {
        width: 80%;
        margin: 1em auto 5em auto;
        i {
            font-size: 6em;
        }
        h3 {
            font-size: 1.8em;
            margin: 0;
        }
        p {
            font-size: 18px;
            padding: 5px 0 20px 0;
            margin: 6px auto;
        }
        a {
            text-transform: uppercase;
        }
    }
}
```
Now the final output of section 3 will look something like this:

![section3](https://github.com/abhishekraj007/topcoder-frontend/blob/master/screenshots/sec3.PNG?raw=true)

<a name="section4">
## Section4 - challenge section

Section 4 of this page contains a `heading` below it a `subheading` and below it a `row` with 4 `cards`. Building exact card is little challenging, But its possible to build similar looking card, Each card have similar structure but with different colour scheme. So, our html markup will look something like this:

```html
    <section>
            <div class="challenge">
                <div class="container">
                    <div class="text-center">
                        <h1>What Can You Do With Crowdsourcing?</h1>
                        <h3>
                            What kind of amazing work has been done recently on topcoder? Have a look at some examples.
                        </h3>
                    </div>
                    <div class="row">
                        <div class="col-md-3 col-xs-12">
                            <div class="card blue-top">
                                <div class="icon-top">
                                    <i class="ion-ios-color-filter-outline blue-back"></i>
                                    <span class="small blue">Mobile design</span>
                                </div><!-- icon-top -->
                                <div class="clearfix"></div>
                                <h3>IBM Castle - Email Client Mobile Design Challenge</h3>
                                <div class="block">
                                    <div class="float-right">
                                        <i class="fa fa-user"></i>&nbsp; 77 &nbsp;
                                        <i class="fa fa-user"></i>&nbsp;25
                                    </div>
                                    <h5>March 2016</h5>
                                </div>
                                <h5>#Mobile Design #Responsive</h5>
                                <div class="block">
                                    <div class="float-right">
                                        <i class="fa fa-user user-round"></i>
                                        <i class="fa fa-user user-round"></i>
                                        <i class="fa fa-user user-round"></i>
                                    </div>
                                    <h2>$2,500</h2>
                                </div>
                                <div class="text-center">
                                    <a href="#" class="btn btn-default">View Challenge</a>
                                </div>
                            </div>  <!-- Card 1-->
                        </div>
                        <!-- col -->
                        <div class="col-md-3 col-xs-12">
                            <div class="card green-top">
                              ....
                            </div> <!-- Card 2-->
                        </div>
                        <div class="col-md-3 col-xs-12">
                            <div class="card orange-top">
                               ....
                            </div> <!-- Card 3-->
                        </div>
                        <div class="col-md-3 col-xs-12">
                            <div class="card green-top">
                               ....
                            </div> <!-- Card 4-->
                        </div>
                    </div> <!-- row -->
                </div>  <!-- container -->
            </div><!-- challenge -->
        </section> <!-- section -->
```
At this point output of this section will look horrible something like this:

![sec4](https://github.com/abhishekraj007/topcoder-frontend/blob/master/screenshots/sec4_1.PNG?raw=true)

But, paste the following css code and see the magic

```css
.challenge {
    background: $brown-light;
    width: 100%;
    height: 100%;
    padding-top: 50px;
    .container {
        width: 80%;
    }
    .col-md-3 {
        padding: 0 10px;
    }
    h1 {
        padding: 30px 0 0 0;
    }
    .card {
        background: $white;
        box-shadow: 0px 0px 5px $brown-text;
        margin: 2em 0;
        padding: 1.5em 1em;
        .icon-top {
            i {
                font-size: 36px;
                border-radius: 100%;
                height: 50px;
                width: 50px;
                float: left;
                color: $white;
                text-align: center;
                display: inline-block;
            }
            .blue-back {
                background: $main;
            }
            .orange-back {
                background: $orange;
            }
            .green-back {
                background: $green;
            }
            .small {
                font-size: 1.1em;
                font-weight: 600;
                text-transform: uppercase;
                float: right;
            }
        }
        i.user-round {
            border-radius: 100%;
            background: #c6c6c6;
            height: 30px;
            font-size: 30px;
            text-align: center;
            width: 30px;
        }
        h3 {
            font-size: 22px;
        }
        h2 {
            font-size: 24px;
        }
        a {
            margin: 1em 0 0 0;
        }
    }
    .blue-top {
        border-top: 6px solid $blue;
    }
    .orange-top {
        border-top: 6px solid $orange;
    }
    .green-top {
        border-top: 6px solid $green;
    }
}

```
Now the output will be similar to this

![sec4_2](https://github.com/abhishekraj007/topcoder-frontend/blob/master/screenshots/sec4_2.PNG?raw=true)

<a name="onepage">
## One page scrolling effect

At this point our all section is ready. But we want similar one page scrolling effect as you see on topcoder website while browsing on big screens. One page at a time with ease effect.

So, to get similar scrolling effect I am going to use a javascript plugin written by [Pete R](http://www.thepetedesign.com/). Find the plugin [here](https://github.com/peachananr/purejs-onepage-scroll)

We will add two more links in our project one `onepage-scroll.css` and another `onepagescroll.js` file.

To work plugin, our page structure should be something like this:

```html
 <div class="main">
    <section>...</section>
    <section>...</section>
    <section>...</section>
    <section>...</section>
  </div>
```

Which we already have, just all one `div` with class `main` outside all `section`. And add following `javascript` code in the project:

```js

  $(document).ready(function() {

      /* Using onePageScroll Plugin by pete R */
      onePageScroll(".main", {
          // sectionContainer accepts any kind of selector in case you don't want to use section
          sectionContainer: "section",
          // Easing options accepts the CSS3 easing animation such "ease", "linear", "ease-in"
          easing: "linear",
          // AnimationTime let you define how long each section takes to animate
          animationTime: 1000,
          // Activate the keyboard controls for up and down navigation
          keyboard: true,
          // the browser's width is less than 1100, the fallback will kick in.
          responsiveFallback: 1100

      });

  });

  /* add and remove class on widow resize for eliminating plugins default behavior like height size, etc  */
  $(window).on('resize', function() {
      var win = $(this);
      if (win.width() < 1100) {

          $('section').removeClass('ops-section');
          $('div').removeClass('border-right');

      }
      else {
          $('section').addClass('ops-section');
      }

  });
  
```

That's it. All Done!  

See the final output [here](https://abhishekraj007.github.io/apps/topcoder)

I have added some extra css code to make this page responsive and remove onepage scrolling effect to get back default scrolling and control heights of the sections on smaller device which can be found in source code of this repo.



<a name="resources">
## Resources

* Topcoder
* Bootstrap
* OnePageScolling plugin

<a name="note">
## Note

ALL of the contents and design used during practice session is the property of topcoder. I don't claim to hold any of the contents/resources. I have used the contents just for the placeholder and design as an inspiration to practice my front-end development skill.