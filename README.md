## Archived
Discussion has moved here: https://github.com/w3c/csswg-drafts/issues/333

# aspect-ratio
This is a repo to explore, and hopefully define a way to maintain aspect ratio

# Usecases

**... see issues, we should end up with a few here ...**

- [Responsive Aspect Ratio with EQCSS](http://elementqueries.com/demos/aspect-ratio.html)

This demo uses a custom `data-ratio=""` attribute in HTML to store an aspect ratio, expressed as `width:height` like `4:3`, or `640:480`, or `16:9`. Using an aspect ratio of `1:1` would have equal height and display as square. This demo uses JavaScript (via EQCSS) to read the `data-ratio=""` attribute and apply it in the CSS for each element.

- [Responsive iframe Scaling](http://elementqueries.com/demos/video-scaling.html)

This demo uses JavaScript (via EQCSS) to read the `width=""` and `height=""` attributes that come by default with the `<iframe>` embed codes from video sites like Youtube and Vimeo. By treating these values as the native width and height of the aspect ratio, the correct aspect ratio can be divined for displaying the video at any width.

This approach is discussed in this article [in the section about evaluating JavaScript inside CSS](https://www.smashingmagazine.com/2016/07/how-i-ended-up-with-element-queries-and-how-you-can-use-them-today/#using-$it-inside-eval)

```
@element 'iframe' {
  $this {
    margin: 0 auto;
    width: 100%;
    height: eval("clientWidth/(width/height)")px;
  }
}
```

- [Pure JS Padding Hack for Youtube/Vimeo Videos](http://codepen.io/tomhodgins/pen/YyarJz)

This demo contains JavaScript that will locate and automatically wrap any `<iframe>` containing content from Youtube or vimeo in an element with the padding hack. It determines the percentage of padding based on the `width=""` and `height=""` attributes included in the `<iframe>` markup in HTML.

- [Gallery Plugin with Responsive Aspect Ratio](http://codepen.io/tomhodgins/pen/rLNerQ)

This is a simple image slideshow that uses a `data-ratio=""` custom attribute in HTML and vanilla JavaScript to apply the correct padding amount. This means that the aspect ratio of the gallery as displayed on the page can vary to match the photos - in our case this value would be rendered in the HTML by the backend via PHP.

- Prevent content pushing from layout reflows by implementing aspect-ratio sized box [demo](http://daverupert.com/2015/12/intrinsic-placeholders-with-picture/)
- Prevent content pushing when `picture` aspect-ratio changes [demo](http://daverupert.com/2012/04/uncle-daves-ol-padded-box/)

# Potential solution
Jonathan Kingston already has a decent proposal here for it to work in CSS: https://jonathankingston.github.io/logical-sizing-properties/#propdef-aspect-ratio

# Meetings
We discussed this issue at TPAC, here are the minutes: http://www.w3.org/2016/09/21-respimg-minutes.html
