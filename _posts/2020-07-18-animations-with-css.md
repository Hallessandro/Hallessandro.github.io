---
layout: post
title: "#19 - An introduction to CSS animation"
author: "Hallessandro D´villa"
categories: programming, css, frontend
tags: [programming, css, frontend]
image: coverPosts/css_animation.png
header-img: "css_animation.png"
---

Hello, in this post we will talk about CSS animation, but before we start I created this simple HTML page and a CSS code to use as example during the explanations, so please copy and paste this in your favorite editor and let's get started. 

<img src="../assets/img/memes/suzumiya.png" alt="suzumiya thumbs up" style="width:400px;"/>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>#19 - CSS Animations</title>
</head>
<body>
    <div class="box">        
        <img src="https://images.smash.gg/images/user/669949/image-c06fd3a089292af4bcadc720c336e2f4.gif" alt="Neko of Melty Blood">
    </div>
</body>
</html>
```

This is the CSS: 

```css
        .box {
            margin-top: 80px;
            background-color: rebeccapurple;
            height: 200px;
            width: 200px;
        }
```

#### CSS animations 

Animations in CSS contains two parts, the keyframe at-rule, which defines an animation and the the animation property, which applies that animation to an element. 

When we use keyframes we need to define at least two things, the name of the animation and the values that specifies when the style will change during the animation, this can be done using percent or the keywords "from" and "to", which is the same that 0% and 100%. 

A basic declaration of keyframe can be seen below: 

```css
        @keyframes move-to-right {
            0%{}

            50% {}

            100% {}
        }
```

First we have "move-to-right" that is the name of the animation and after this we have three values in percentage, where 0% it's the beginning of the animation, 50% it's half away and 100% it's the end of the animation. 

We can define how many values we want between 0% and 100%, for example: 

```css
        @keyframes change-background {
            0%{ background-color: blue; }

            10% { background-color: green; }            
            25% { background-color: red; }            
            39% { background-color: black; }            
            50% { background-color: white; }            
            75% { background-color: purple; }            

            100% { background-color: yellow; }
        }
```

After created the keyframe, we need to use the animation property to in fact use our animation, for this let's add some css code to the style of the box created before. 

```css
        .box {
            margin-top: 80px;
            background-color: rebeccapurple;
            height: 200px;
            width: 200px;

            animation-name: move-to-right;
        }
```

Ok now we need to add some code inside the keyframe move-to-right because currently it's empty. Let's use the transform property do move the element to the right, as the name of the animation say. 

```css
        @keyframes move-to-right {
            0%{
                transform: translate(0px);
            }

            50% {
                transform: translate(150px) scale(1.5);
            }

            100% {
                transform: translate(0px);
            }
        }
```

At the beginning of the animation (0%) nothing happens, but at the 50% the element will be moved 150px to the right and your scale will be increased in 1.5x, after that in the end of the animation the element go back to the original position. It’s A Piece Of Cake. 

Now open the browse and see if your animation worked... 

Nothing happened right? This occurs because besides declaring the animation-name we need to inform the duration of our animation, and this can be done using animation-duration whose the default value is zero, and this is because nothings happened. 

Below animation-name add animation-duration:4s, and open your browser again, now the animation works perfectly.

```css
        .box {
            margin-top: 80px;
            background-color: rebeccapurple;
            height: 200px;
            width: 200px;

            animation-name: move-to-right;
            animation-duration: 4s;
        }
```

In animation-duration we need to inform how many seconds the animation should it take, in our case 4s (Fell free to add any other value you want). 

Another two useful properties present in animation, are delay and iteration count, where the first one is used to applied a delay before the start of the animation run, and the second is used to inform how many times the animation should be repeted. Let's add both to our CSS. 

```css
        .box {
            margin-top: 80px;
            background-color: rebeccapurple;
            height: 200px;
            width: 200px;

            animation-name: move-to-right;
            animation-duration: 4s;
            animation-delay: 2s;
            animation-iteration-count: 1;
        }
```

To demonstrate better this two properties, let's do a little change in our keyframe: 

```css
        @keyframes move-to-right {
            0%{
                transform: translate(0px);
                opacity: 0;
            }

            50% {
                transform: translate(150px) scale(1.5);
                opacity: 1;
            }

            100% {
                transform: translate(0px);
                background-color: black;
            }
        }
```

Now at the beginning of the animation our box should be invisible and at end the background color of the box, shoud be black.

At the beginning of the animation in fact the image will disappear, but because we define a delay when the page is loaded the image will be visible and just after the 2s it will become invisible, this is not what we want.

At the end of the animation we will see another problem, our background has been restored to the original color, this happens because all the changes in the CSS made inside a keyframe has value only during animation.   

To solve this two problems we need to use another animation property called fill-mode. This property is used to define when the animation styles shoud be applied. The default value is none what means the the styles just are applied during the animation, and nothing happens before or after.

There are six values as options to animation-fill-mode, none (default), forwards, backwards, both, initial and inherit. 

1. None as we already see don't do anything and the styles just are applied during the animation. 

2. Forwards and backwards on the other hand retain the style values set by the last and the first keyframe respectively.

3. Both means forwards and backwards, extending the animation properties in both directions. 

4. Initial sets this property to its default value.

5. Inherit Inherits this property from its parent element.

To solve our problem we can use **both**, this means that the opacity declaration in 0% will be applied just aftet the page loaded and the background color in 100%, will still working after the end of the animation. 

```css
        .box {
            margin-top: 80px;
            background-color: rebeccapurple;
            height: 200px;
            width: 200px;

            animation-name: move-to-right;
            animation-duration: 4s;
            animation-delay: 2s;
            animation-iteration-count: 1;
            animation-fill-mode: both;
        }
```

One more thing, change the value of animation-iteration-count to something bigger that 1 and open the page again. Now you will see that the animation will be repeated as many times informed in iteration-count. The default value for this property is 1, so if you don't want to repeat the animation you don't need to declare this property.

So I think it's good for today, thanks for read and see you next time. 

<img src="../assets/img/memes/34663.gif" alt="Konosuba dancing" style="width:400px;"/>