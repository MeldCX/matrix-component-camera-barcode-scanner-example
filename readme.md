# MeldCX Matrix Camera Barcode Scanner Web Component

## Getting started

1. To install the npm module `@meldcx/matrix-component-camera-barcode-scanner`

2. Add the following scripts inside the `<head></head>` of your html page.

3. Include the MeldCX Agent library `<script src="https://storage.googleapis.com/assets.meld.cx/agent/1.0.18/Agent.js"></script>`

4. Add a reference to the script `<script src="node_modules/@meldcx/matrix-component-camera-barcode-scanner/dist/index.js"></script>`

## Listening for Barcodes

1. Add the `m-camera-barcode-scanner` component to your html page, `<m-camera-barcode-scanner width="800" height="600"></m-camera-barcode-scanner>`
2. Additional attributes can be added to the `m-camera-barcode-scanner` component. See below for more information:
    - example: `<m-camera-barcode-scanner width="800" height="600" resHeight="1920" resWidth="1080" qrHeight="300" qrWidth="300"></m-camera-barcode-scanner>`
    - resHeight: max resolution height of the attached camera (in the example we use 1920)
    - resWidth: max resolution width of the attached camera (in the example we use 1080)
    - qrHeight: Height of the QR bounding box overlay, used to improve ease of use for QR scanning
    - qrWidth: Width of the QR bounding box overlay, used to improve ease of use for QR scanning
3. Using the `document.querySelector` function, locate the element and store it as an object `const reader = document.querySelector('m-camera-barcode-scanner');`
4. Listen for Barcode events, `reader.addEventListener('result', ({data}) => console.info(data));`
5. Pause/Play functionality is outlined in the Matrix Camera Barcode Scanner example application, using the function available in index.html e.g.
```
    document.querySelector('#play-pause');
    button.addEventListener('click', () => {
        if (reader.stop) {
          reader.play();
          button.textContent = 'Pause';
        } else {
          reader.pause();
          button.textContent = 'Play';
        }
    });
 ```
A button will be displayed once camera is allowed on device. Press pause to stop the video. Once video has stopped, press play and allow access to the camera again. The video will resume playing.

