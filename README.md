# [Antivertical](https://git.svoboda.works/svoboda/antivertical) logotype

1. Pure CSS 🤟
2. Insane speed ⚡️
3. Real time tuning 🛹 
4. It is not a sharingan

see you later<br>
[Antivertical](https://git.svoboda.works/svoboda/antivertical), [CodePen](https://codepen.io/mirzaev-sexy/pen/zxxPgyw)

## Demonstration
![logotype_optimized_looped.gif](/assets/logotype_optimized_looped.gif)

## Code 
```html
<svg id="antivertical">
  <circle class="node" />
  <circle class="node" />
  <circle class="node" />
  <circle class="core" />
  <circle class="core" />
  <circle class="core" />
  <mask id="synapse_mask">
    <rect fill="white" width="100%" height="100%" />
    <circle class="node" />
    <circle class="node" />
    <circle class="node" />
  </mask>
  <circle class="synapse" mask="url(#synapse_mask)" />
</svg>
```

```css
@-webkit-keyframes rotating {
  from {
    -webkit-transform: var(--scale) rotate(0deg);
    -o-transform: var(--scale) rotate(0deg);
    transform: var(--scale) rotate(0deg);
  }

  to {
    -webkit-transform: var(--scale) rotate(360deg);
    -o-transform: var(--scale) rotate(360deg);
    transform: var(--scale) rotate(360deg);
  }
}

@keyframes rotating {
  from {
    -ms-transform: var(--scale) rotate(0deg);
    -moz-transform: var(--scale) rotate(0deg);
    -webkit-transform: var(--scale) rotate(0deg);
    -o-transform: var(--scale) rotate(0deg);
    transform: var(--scale) rotate(0deg);
  }

  to {
    -ms-transform: var(--scale) rotate(360deg);
    -moz-transform: var(--scale) rotate(360deg);
    -webkit-transform: var(--scale) rotate(360deg);
    -o-transform: var(--scale) rotate(360deg);
    transform: var(--scale) rotate(360deg);
  }
}

body {
  margin: unset;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

svg#antivertical {
  --core-radius: 7px;
  --node-radius: 14px;
  --node-stroke: 2px;
  --width: 75px;
  --length: calc(var(--width) - (var(--node-radius) + var(--node-stroke)) * 2);
  --bisector: calc((var(--length) * sqrt(3)) / 2);
  --height: calc(
    var(--bisector) + (var(--node-radius) + var(--node-stroke)) * 2
  );
  --x1: calc(var(--node-radius) + var(--node-stroke));
  --y1: calc(var(--node-radius) + var(--node-stroke));
  --x2: calc(var(--width) - var(--node-radius) - var(--node-stroke));
  --y2: calc(var(--node-radius) + var(--node-stroke));
  --x3: calc(var(--width) / 2);
  --y3: calc(var(--bisector) + (var(--node-radius) + var(--node-stroke)));
  --scale: scale(2);
  --center-x: calc((var(--x1) + var(--x2) + var(--x3)) / 3);
  --center-y: calc((var(--y1) + var(--y2) + var(--y3)) / 3);
  --rotate: rotating 6s linear infinite;
  width: var(--width);
  height: var(--height);
  transform-origin: var(--center-x) var(--center-y);
  -webkit-animation: var(--rotate);
  -moz-animation: var(--rotate);
  -ms-animation: var(--rotate);
  -o-animation: var(--rotate);
  animation: var(--rotate);
}

svg#antivertical > circle.synapse {
  cx: var(--center-x);
  cy: var(--center-y);
  r: calc(var(--length) / 2.1);
  stroke-width: calc(var(--core-radius) * 0.9);
  stroke: black;
  fill: transparent;
}

svg#antivertical > circle.node,
svg#antivertical > mask > circle.node {
  r: var(--node-radius);
  stroke-width: var(--node-stroke);
  stroke: #000;
  fill: transparent;
}

svg#antivertical > mask > circle.node {
  fill: black;
}

svg#antivertical > circle.core {
  r: var(--core-radius);
  fill: black;
}

svg#antivertical > circle.node:nth-of-type(1),
svg#antivertical > circle.core:nth-of-type(4),
svg#antivertical > mask > circle.node:nth-of-type(1) {
  cx: var(--x1);
  cy: var(--y1);
}

svg#antivertical > circle.node:nth-of-type(2),
svg#antivertical > circle.core:nth-of-type(5),
svg#antivertical > mask > circle.node:nth-of-type(2) {
  cx: var(--x2);
  cy: var(--y2);
}

svg#antivertical > circle.node:nth-of-type(3),
svg#antivertical > circle.core:nth-of-type(6),
svg#antivertical > mask > circle.node:nth-of-type(3) {
  cx: var(--x3);
  cy: var(--y3);
}
```
