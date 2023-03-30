# EJS_ChromaEditor

Dedicated browser for working with the Web Chroma Editor

## Resources

[Electron Forge - Getting Started](https://www.electronforge.io/)

## Setup

Create the EJS Forge Project.

```cli
npm init electron-app@latest EJS_ChromaEditor
```

Change the start url in [src/index.html](src/index.html)

```html
<!DOCTYPE html>
<html>
  <head>
  <script>
    window.location = 'https://chroma.razer.com/ChromaEditor/';
  </script>
  </head>
</html>
```

Update window defaults in [src/index.js](src/index.js) to change the default window size, maximize, and disable opening the default dev tools

```js
const createWindow = () => {
  // Create the browser window.
  const mainWindow = new BrowserWindow({
    width: 1280,
    height: 720,
    webPreferences: {
      preload: path.join(__dirname, 'preload.js'),
    },
  });

  // and load the index.html of the app.
  mainWindow.loadFile(path.join(__dirname, 'index.html'));

  // Open the DevTools.
  // mainWindow.webContents.openDevTools();

  // maximize the window
  mainWindow.maximize();
  mainWindow.show();
};
```

Start the app to verify the application works

```cli
CD EJS_ChromaEditor
npm start
```

Build the standalone application

```cli
npm run make
```

Application outputs to `out\ejs-chromaeditor-win32-x64\ejs-chromaeditor.exe`

Build the installer

```cli
npm run publish
```

Installer outputs to `out\make\squirrel.windows\x64\ejs-chromaeditor-1.0.0 Setup.exe`
