CircularTools
==============

Readme and code is under development.

Circle based animations for Android (min. API 11)

Currently implemented:
- Circular reveal
- Circular transform

Planned:
- Radial action

//TODO gifs

Sample
======
<a href="https://github.com/Gordi90/CircularTools/releases"> //TODO releases</a>

Note
======
- it's a fork from https://github.com/ozodrukh/CircularReveal/
- independent from Jake Wharton's NineOldsAndroid
- the returned `animator` is an `ObjectAnimator` so you can reverse it.
 
Limitations
======
- it will never use the native `ViewAnimationUtils.createCircularReveal` 
- hardware acceleration cannot be used in every situation. See table below:

|           | API 11-17 | API 18-19 |   19+    |
|-----------|-----------|-----------|----------|
|   **Reveal**  |  Software |  Hardware | Software |
| **Transform** |  Software |  Hardware | Hardware |

Using
======

For reveal and transform you have to wrap your animated views with a `CircularFrameLayout`.

```xml
<hu.aut.utillib.circular.widget.CircularFrameLayout
        android:id="@+id/simple_reveal"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
    <!-- Put any child views here if you want, it's stock frame layout  -->

</hu.aut.utillib.circular.widget.CircularFrameLayout>
```
**Transform:**
```java
//myTargetView & mySourceView are children in the CircularFrameLayout
float finalRadius = CircularAnimationUtils.hypo(width, height);

//getCenter computes from 2 view: One is touched, and one will be animated, but you can use anything for center
int[] center = CircularAnimationUtils.getCenter(fab, myTargetView);

animator = CircularAnimationUtils.createCircularTransform(myTargetView, mySourceView, center[0], center[1], 0F, finalRadius);
animator.setInterpolator(new AccelerateDecelerateInterpolator());
animator.setDuration(1500);
animator.start();

```

**Reveal:**
```java
//myView is a child in the CircularFrameLayout
float finalRadius = CircularAnimationUtils.hypo(width, height);

//getCenter computes from 2 view: One is touched, and one will be animated, but you can use anything for center
int[] center = CircularAnimationUtils.getCenter(fab, myView);

animator = CircularAnimationUtils.createCircularReveal(myView, center[0], center[1], 0, finalRadius);
animator.setInterpolator(new AccelerateDecelerateInterpolator());
animator.setDuration(1500);
animator.start();      

```

How to add dependency
=====================

This library is not released in Maven Central, but instead you can use [JitPack](https://www.jitpack.io/)

add remote maven url

```groovy
	repositories {
	    maven {
	        url "https://jitpack.io"
	    }
	}
```

then add a library dependency

```groovy
	dependencies {
	    compile '//TODO'
	}
```


License
--------

    The MIT License (MIT)

    Copyright (c) 2015 AutSoft Kft.
    
    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in
    all copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
    THE SOFTWARE.
