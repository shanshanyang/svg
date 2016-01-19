# SVG: Scalable Vector Graphics

- resolution-independence
- SVG images come with an alpha channel and do not suffer from any problems when they are used on different background colors.
- The number of colors the GIF goes through is limited by its number of frames.

## Hand code a simple SVG

Github Forkme banner
http://codepen.io/andreayang/pen/zrEzpe

## Where to use SVG

- Logos
- non-complex
- vector-based illustrations
- user interface controls
- infographics
- icons

## Ways to use SVG
- Image tag

`<img src="forkme.svg" alt="Github Forkme banner">`

- Background Image

`
.banner {
    background: url(forkme.svg);
}
`
- Inline SVG

`<svg>...</svg>` in markup

- SVG in <object>

`<object type="image/svg+xml" data="forkme.svg" class="banner">..</object>`

## Pro & Cons of these methods
'inline svg' advantages
- saves HTTP Requests

'inline svg' disadvantages 
- "bloated" document
- inability to cache.

Note: gzip and cache the document.

## Browser Support
Supported across all Modern Browsers

- Image tag: http://caniuse.com/#feat=svg-img
- Background Image: http://caniuse.com/#feat=svg-css
- Inline svg: http://caniuse.com/#feat=svg-html5

## CSS with SVG
- use class 
- inline style: `<svg> <style>...</style>...</svg>`
- external style: add `<?xml-stylesheet type="text/css" href="svg.css" ?>` right before `<svg>` in forkme.svg file. then use`<object type="image/svg+xml" data="forkme.svg">..</object>` in html

## SVG as dataURI
- `<img src="data:image/svg+xml;base64,[data]">`
- `<object type="image/svg+xml" data="data:image/svg+xml;base64,[data]">fallback</object>`

## Efficient data format for dataURI svg
- `<!-- base64 -->`
- `<!-- UTF-8, not encoded -->`
- `<!-- UTF-8, optimized encoding for compatibility -->`
- `<!-- Fully URL encoded ASCII -->`

## How is SVG rendered in browser

## SVG animation

Techniques:
- [Native] CSS @keyframes
- [Native] SMIL (Synchronized Multimedia Integration Language)
- [Library] Velocity.js
- [Library] GreenSock (GSAP)
- [Library] snap.svg
- [Library] Raphaël

CSS keyframes
- good performance when hardware accelerated
- No integration cost to existing UI systems
- Chaining multiple animations is done with delays
- limited user interaction types
- Physics can be cumbersome. Complicated tasks like friction, or a progressive decreasing bouncing ball are extremely complex at best and not an option at worst.
- Percentage based timing is harder to manipulate than its JavaScript counterpart because it adds a layer of abstraction.
- `transform-origin` for SVG is not consistent:
Stacking transforms one after another is not intuitive, as it responds to the last placement of the element.
It does not show consistent behavior from browser to browser.

SMIL
- Declarative syntax
- Can morph paths and shapes using the same syntax with which it was written, which makes it very intuitive. This is nice for things like logos or morphing button icons.
- Animate along path
- Performs very well, arguably better than CSS, Velocity, and GSAP in terms of visual display.
- non-delay based chaining like beginning an animation when another ends.
- Easy to add to existing SVG syntax and no need to load external resources.
- Browser Support (No IE/Edge support and Currently not planned): http://caniuse.com/#feat=svg-smil
- Chained animations are fairly limited.

Velocity.js
- jQuery like syntax
- many out-of-the-box easings
- can stagger multiple animations with one line of code
- Deeper browser support than CSS
- Performance is below CSS, SMIL, or GSAP
 
GreenSock
- Easy to use and the most compact syntax.
- timeline: easily control and manipulate sequenced animation
- Automatically hardware accelerated. Performance is extremely good — as good as native rendering.
- Applying physics is simple
- Their code is open source, but you might need a license for commercial use in certain situations.

Recommendations for use:

- Use *CSS* animations for small transitions or simple animations. You need not load another resource, and small transforms on hover can be a boon for interaction and UX. Particularly when you don't need physics or to do a lot of stacking SVG transforms, which are not always necessary.
- Use *SMIL* for morphing SVGs into one another in the case of logos, etc., and when the thing being animated can fallback to a stagnant image in IE.
- Use *Velocity* for a performance boost on existing jQuery animations without having to change a lot of code.
- Use *GSAP* for highly performant animations or longer-scale animations that have multiple scenes. It solves major issues with browser-to-browser consistency for SVG transform origin. GSAP is very robust with a broad feature-set, but you can use smaller versions without a lot of bells and whistles, loading only what is necessary.

## Performance Benchmark of SVG Animation

- http://codepen.io/collection/ArxBLz/
- https://www.youtube.com/watch?v=1ZWugkJV5Ks
- measure methods: 
    - one based on the Chrome DevTools timeline recordings
    - one based on visual recordings off of the screen

## Hardware accelerated animation

#### How to hardware accelerate with CSS

Setting transforms to null, and then moving them with transforms.
You're offloading them to the GPU (Graphics Processing Unit). Most modern browsers ship with hardware acceleration, but don't use it until they are told they need to.
Other GPU acceleration: `backface-visibility: hidden;` and `perspective: 1000;`- keeps the animation from flickering.
Isolate the layer you need to move or adjust.
Move with transforms.
#### How to hardware accelerate with SMIL

Use `<animateTransform>` instead of `<animate>` and set x, y, z values (with 0 for z).
Similar to CSS, this moves the element off to its own layer. Moving with transforms performs better than margins or top, left because it doesn't repaint.
#### How to hardware accelerate with Velocity

Move with `translateX` and `translateY`. Set the element to `translateZ: 0;`.
Make sure to avoid layout thrashing by declaring a variable for elements that you animate more than once to prevent multiple lookups (not applicable here but worth mentioning).
#### How to hardware accelerate with GSAP

In the demo we set the element to force3D: "true", but GSAP now ships with this automatically in place. This means you don't have to use `translateZ: 0;` to hardware accelerate, it’s already included.
Moving objects with X and Y perform better than margins.
TweenLite is the lighter-weight version of GSAP, and it's recommended to use this for smaller animations. TweenMax offers support for loops, so we use it here.

## SVG optimization

tools: 

- https://github.com/svg/svgo
- http://petercollingridge.appspot.com/svg-editor

## Accessibility of SVG
SVGs are accessible; text and drawing elements are machine-readable so screen readers can other devices can parse the images.

## Automation to create a svg or svg sprite


## SVG vs Gif

- https://sarasoueidan.com/blog/svg-vs-gif/ 

## SVG vs Icon Font

http://www.creativebloq.com/web-design/icon-fonts-vs-svg-101413211


## Graphics file format

- https://en.wikipedia.org/wiki/Raster_graphics
- https://en.wikipedia.org/wiki/BMP_file_format


## Resources
- https://css-tricks.com/weighing-svg-animation-techniques-benchmarks/
- https://sarasoueidan.com/blog/svg-tips-for-designers/
- https://24ways.org/2014/an-overview-of-svg-sprite-creation-techniques/
- https://www.w3.org/Graphics/SVG/IG/resources/svgprimer.html
- https://en.wikipedia.org/wiki/Scalable_Vector_Graphics
- http://lea.verou.me/
- https://sarasoueidan.com/
- https://css-tricks.com/guide-svg-animations-smil/
- VML: https://www.w3.org/TR/NOTE-VML
- https://www.w3.org/Graphics/SVG/

## Follow them for more SVG stuff
Sara Soueidan @SaraSoueidan
Sarah Drasner: https://css-tricks.com/author/sdrasner/

