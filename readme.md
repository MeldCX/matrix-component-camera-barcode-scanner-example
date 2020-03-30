<img src="https://dev-marketing.meld.cx/wp-content/uploads/2018/04/logo-400.png" width="20%" >

# MeldCX Matrix Camera Barcode Scanner Web Component

## Getting started

1. To install the npm module `@meldcx/matrix-component-camera-barcode-scanner`

2. Add the following scripts inside the `<head></head>` of your html page.
```
    ...
    <head>
        <!-- MeldCX Agent Library -->
        <script src="https://storage.googleapis.com/assets.meld.cx/agent/1.0.41/Agent.js"></script>

        <!-- MeldCX Barcode Scanner Component -->
        <script src="node_modules/@meldcx/matrix-component-camera-barcode-scanner/dist/index.js"></script>
    </head>
    ...
```
## Listening for Barcodes

1. Add the `m-camera-barcode-scanner` component to your html page
```
    <m-camera-barcode-scanner width="800" height="600"></m-camera-barcode-scanner>
```
2. Using the `document.querySelector` function, locate the element and store it as an object
```
    const reader = document.querySelector('m-camera-barcode-scanner');
```
3. Listen for Barcode events,
```
    reader.addEventListener('result', ({data}) => console.info(data));
```
4. Start scanning
```
    reader.startScanning(true) // passing 'true' calls reader.play() if the video is not streaming
```


## Methods

| async | Method Name    | Description                                   | Arguments                                                                                          |
| ----- | -------------- | --------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| no    | pause          | Stops scanning and pauses video stream        | N/A                                                                                                |
| yes   | play           | Starts video stream                           | `videoTrack` (number) <br> - the index of the video track to use.<br>Defaults: `this.track` or `0` |
| no    | stopScanning   | Stops scanning but keeps video stream playing | N/A                                                                                                |
| yes   | startScanning  | Starts scanning                               | `force` (true/false) <br> - calls play() if not already playing                                    |
| yes   | getQRCode      | Simple method to get first valid QR code      | `force` (true/false) <br> - calls startScanning(force) if not already scanning                     |
| no    | getTrackLabels | Returns list of cameras                       | N/A                                                                                                |
| no    | setTrack       | Sets `this.track`                             | `videoTrack` (number) <br> - the index of the selected track name                                  |

## Events

| Event name | Triggering Event               | Data                    |
| ---------- | ------------------------------ | ----------------------- |
| result     | a valid QR code is found       | `{ text: /*QR data*/ }` |
| pause      | video track is paused          | `{}`                     |
| play       | video track is resumed/started | `{}`                     |
| scanStop   | scanning is stopped            | `{}`                     |
| scanStart  | scanning is started            | `{}`                     |

## Attributes

| Attribute Name          | Values          | Default   | Description                                                                                                                  |
| ----------------------- | --------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------- |
| auto-start              | `play` `scan`   | `nil`     | if specified, the video will start playing/scanning on load                                                                  |
| frame-rate              | `<number>`      | `30`      | the frame-rate used in [applyContraints](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/applyConstraints) |
| guide                   |                 | `nil`     | if present, the guide will be visible when scanning                                                                          |
| guide-size              | `<number>`      | `auto`    | the size of the guide. Only this area will be scanned                                                                        |
| guide-invalid-color     | `<color value>` | `#2BCC61` | the color of the guide when no valid qr code is present                                                                      |
| guide-valid-color       | `<color value>` | `#FF4248` | the color of the guide when a valid qr code is present                                                                       |
| height                  | `<number>`      | `720`     | the height used in [applyContraints](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/applyConstraints)     |
| width                   | `<number>`      | `1280`    | the width used in [applyContraints](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/applyConstraints)      |
| idle-camera             |                 | `nil`     | if present, pausing the stream keeps the camera active but stops the video track. Makes frequent pausing/playing faster      |
