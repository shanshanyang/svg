# SVG: Scalable Vector Graphics

## Hand code a simple SVG

Github Forkme banner
http://codepen.io/andreayang/pen/zrEzpe

## Use SVG
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
Supported across all Mordern Browsers

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


## Performance impact of SVG

## SVG optimization
tools: 
- https://github.com/svg/svgo
- 

## Accessibility of SVG
SVGs are accessible; text and drawing elements are machine-readable so screen readers can other devices can parse the images.

## Automation to create a svg or svg sprite

## Resources to learn about SVG
- https://www.w3.org/Graphics/SVG/IG/resources/svgprimer.html
- 

