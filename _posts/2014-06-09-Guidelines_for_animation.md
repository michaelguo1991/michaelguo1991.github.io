---
layout: post
title: Guidelines for animation
tags: performance css animation
---

**Guidelines for animation**

1. Use CSS keyframe animation or CSS transitions, if at all possible. The browser can optimize painting and compositing bigtime here.
2. If needs to be it’s JS-based animation, use requestAnimationFrame. Avoid setTimeout, setInterval.
3. Avoid changing inline styles on every frame (jQuery animate()-style) if you can, declarative animations in CSS can be optimized by the browser way more.
4. Using 2D transforms instead of absolute positioning will typically provide better FPS by way of smaller paint times and smoother animation.
5. Use Timeline Frame’s mode to investigate what is slowing down your behavior
6. “Show Paint Rects” and “Render Composited Layer Borders” are good pro-moves to verify where your element is being rendered.

原文链接：[http://www.paulirish.com/2012/why-moving-elements-with-translate-is-better-than-posabs-topleft/](http://www.paulirish.com/2012/why-moving-elements-with-translate-is-better-than-posabs-topleft/)