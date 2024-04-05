# clickolas-cage

> a chrome extension that performs web browsing actions autonomously to complete a given goal/task (using LLM as a brain).

![image](https://github.com/aj47/clickolas-cage/assets/8023513/3c358fb4-480d-4e6c-87d8-e0e7f709075d)

## Installing

1. Check if your `Node.js` version is >= **14**.
2. Run `npm install` to install the dependencies.
3. you need to either be running a local model on `http://localhost:1234` or change the openAI config in `src/utils.js`

## Developing

run the command

```shell
$ cd clickolas-cage

$ npm run dev
```

1. set your Chrome browser 'Developer mode' up
2. click 'Load unpacked', and select `clickolas-cage/build` folder

The main source files are:
- `src/popup/popup.jsx` The popup window that shows when you press the extension icon
- `src/background/background.js` Persists and facilitates planning
- `src/contentScript/contentScript.js` Executes on web pages, executes actions and scrapes elements
- `src/utils.js` Helper functions

### Current Flow
1. User clicks extension icon, enters and submits goal prompt
2. Popup.jsx sends a message to background.js with request type 'new_goal'
3. background.js calls promptToFirstStep() in utils.js
4. LLM returns starting URL which feeds into navURL()
5. navURL will open a new tab with the starting URL
6. getNextStep() is called which will get contentScript to extract clickable elements and send it to LLM to generate next step




## Packing

After the development of your extension run the command

```shell
$ npm run build
```

Now, the content of `build` folder will be the extension ready to be submitted to the Chrome Web Store. Just take a look at the [official guide](https://developer.chrome.com/webstore/publish) to more infos about publishing.

---

Generated by [create-chrome-ext](https://github.com/guocaoyi/create-chrome-ext)
