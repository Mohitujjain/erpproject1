https://solid-goggles-6wg4w9wr9ww24pqj.github.dev/

<img width="1265" height="706" alt="image" src="https://github.com/user-attachments/assets/b575dec1-413e-49e4-a88d-9802c0c7c6ba" />






1 Install Linux Wine (Fixes the .exe Error)
--------------------------------------------

* Run this first in the Codespaces terminal to allow Linux to build Windows software.

Copy below code and paste it under terminal after html code :
--------------------------------------------------------------
sudo dpkg --add-architecture i386 && sudo apt-get update && sudo apt-get install -y wine wine32 wine64

Note: Combined into one line for easy copying! Just paste and press Enter. Wait 1-2 mins to finish.

2
Initialize NPM & Install Electron
----------------------------------
Setup the project and install the Electron builder engines.

Copy:
------
npm init -y && npm install electron --save-dev && npm install electron-builder --save-dev

After 2nd line of code paste terminal you need to edit html code and replace // Your web app's Firebase configuration in code with your own credentials then enter 3rd step in terminal .
Also need to create account if have not  .

3
Create main.js
----------------
Create a file named main.js and paste this code inside.

Copy:-
-------
const { app, BrowserWindow } = require('electron');

function createWindow () {
  const win = new BrowserWindow({
    width: 1280,
    height: 800,
    autoHideMenuBar: true,
    webPreferences: {
      nodeIntegration: true,
      contextIsolation: false
    }
  });

  win.loadFile('index.html');
}

app.whenReady().then(() => {
  createWindow();
  app.on('activate', () => {
    if (BrowserWindow.getAllWindows().length === 0) createWindow();
  });
});

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') app.quit();
});

Above all at it is just change or replace complete package.json file .

4
Replace package.json
----------------------
Delete everything inside package.json and paste this.
-----------------------------------------------------
Copy
{
  "name": "vortexx-erp-system",
  "version": "1.0.0",
  "description": "Desktop ERP Management System",
  "main": "main.js",
  "scripts": {
    "start": "electron .",
    "build": "electron-builder --win"
  },
  "build": {
    "appId": "com.vortexx.erp",
    "productName": "Vortexx ERP System",
    "win": {
      "target": "nsis"
    }
  },
  "author": "mohit",
  "license": "ISC",
  "devDependencies": {
    "electron": "^31.0.0",
    "electron-builder": "^24.13.3"
  }
}


5
Build the .exe File

Run this final command to compile your Windows software.

Copy:-
----------

npm run build

File will appear inside the dist folder
