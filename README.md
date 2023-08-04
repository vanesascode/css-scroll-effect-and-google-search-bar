## 🔷Favicon Ico

With this project I learned that sometimes having a file called favicon.ico is not cool for your index.html file. I ended up keeping the png extension so it worked.

A favicon can actually be either a PNG, GIF, or ICO file.

## 🔷Google Search Bar

This is the recipe for your search bar to search in google:

- action: "https://www.google.com/search"
- name: q

```
          <form

            action="https://www.google.com/search"
            method="get"
            target="_blank"
            role="search"
          >
            <input
              type="search"
              name="q"
            />
            <button type="submit">Search</button>
          </form>
```

Notice that the search bar appears in the navbar only when the screen is wide and at the bottom only when it is set to mobile size.

## 🔷CSS

### Title Background

I wanted to put a background picture with opacity but without affecting the `<h1>` element. So I used the CSS `::before` pseudo-element.

```
***html

<div class="cover">
  <h1>Understanding the Kernel: The Core of Operating Systems</h1>
</div>

***css

.cover {
position: relative;
}
.cover::before {
content: "";
background-image: url(media/background-keyboard.jpg);
background-repeat: no-repeat;
background-size: cover;
opacity: 0.3;
position: absolute;
top: 0;
left: 0;
right: 0;
bottom: 0;
z-index: -1;
}
```

- We use the `::before` pseudo-element to create a layer behind the content. The `::before` pseudo-element has an absolute position and covers the entire parent `<div>`.

- By setting the `z-index` to -1, it ensures that the background picture stays behind the content.

-Finally, we apply the desired opacity to the background image using the `opacity` property.

With this approach, the opacity will only affect the background picture, leaving the `<h1>` element unaffected.

### Images Scroll Effect

I used some of the latest css tools to make the images appear gradually as you scroll the page:

```
@keyframes show {
  from {
    opacity: 0;
    scale: 25%;
  }

  to {
    opacity: 1;
    scale: 100%;
  }
}

img {
  view-timeline-name: --image;
  view-timeline-axis: block;

  animation-timeline: --image;
  animation-name: show;

  animation-range: entry 25% cover 30%;
  animation-fill-mode: both;
}
```

1.  The code starts by defining a keyframe animation named "show" using the @keyframes rule. This animation has two keyframes: "from" and "to".
2.  The "from" keyframe specifies the initial state of the animation, which is set to an opacity of 0 and a scale of 25%.
3.  The "to" keyframe specifies the final state of the animation, which is set to an opacity of 1 and a scale of 100%.

After defining the keyframe animation, the code selects all "img" elements using the CSS selector.

5.  The view-timeline-name property is used to assign the "--image" timeline name to the selected "img" elements. This timeline name is used to group related animations together.
6.  The view-timeline-axis property is set to "block" for the "img" elements. This property determines the axis along which the animation will be applied. In this case, it is applied vertically.
7.  The animation-timeline property is used to assign the "--image" timeline to the selected "img" elements. This property specifies the timeline to which the animation belongs.
8.  The animation-name property is set to "show" for the "img" elements. This property specifies the name of the animation to be applied.
9.  The animation-range property is used to define the timing and range of the animation. In this case, the animation starts at 25% of the timeline and covers 30% of the timeline.
10. The animation-fill-mode property is set to "both" for the "img" elements. This property determines how the animation applies styles before and after it is executed. "Both" means that the styles defined in the keyframes are applied at the start and end of the animation.
