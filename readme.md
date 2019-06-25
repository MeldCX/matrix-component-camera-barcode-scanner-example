# MeldCX Matrix Camera Barcode Scanner Web Component

## Getting started

1. To install the npm module `@meldcx/matrix-component-camera-barcode-scanner`

2. Add the following scripts inside the `<head></head>` of your html page.

3. Include the MeldCX Agent library `<script src="https://storage.googleapis.com/assets.meld.cx/agent/1.0.18/Agent.js"></script>`

4. Add a reference to the script `<script src="node_modules/@meldcx/matrix-component-camera-barcode-scanner/dist/index.js"></script>`

## Listening for Barcodes

1. Add the `m-camera-barcode-scanner` component to your html page, `<m-camera-barcode-scanner width="800" height="600"></m-camera-barcode-scanner>`
2. Using the `document.querySelector` function, locate the element and store it as an object `const reader = document.querySelector('m-camera-barcode-scanner');`
3. Listen for Barcode events, `reader.addEventListener('result', ({data}) => console.info(data));`