Forked from [original](https://github.com/marko-js-samples/marko-widgets-lasso)
and moved `src/components` to `node_modules/my-components`

The page still loads and number-spinner template still loads, but it gives this error on page load:

    Uncaught Error: Cannot find module "/$/my-components/components/number-spinner" from "/$/marko-widgets/lib"
    raptor-modules-client.js:65
    moduleNotFoundError  @ raptor-modules-client.js:65
    require              @ raptor-modules-client.js:562
    instanceRequire      @ raptor-modules-client.js:110
    load                 @ registry.js:32
    getWidgetClass       @ registry.js:50
    exports.createWidget @ registry.js:76
    initWidget           @ init-widgets-browser.js:98
    initWidgetFromEl     @ init-widgets-browser.js:258
    doInit               @ init-widgets-browser.js:347
    domReadyCallback     @ ready.js:33
    domReady             @ ready.js:51
    domContentLoaded     @ ready.js:65

And on clicking it gives this error

    Uncaught Error: Widget not found: w0

---


In the original version, during load time, a particular instance in call stack shows this:

![http://i.imgur.com/x44bFFe.png]()

    var type = el.getAttribute('data-widget');
    // type = "/src/components/number-spinner"

[Same thing in this forked version shows](http://i.imgur.com/GF5eZom.png)

    var type = el.getAttribute('data-widget');
    // type = "/$/my-components/components/number-spinner"

If these paths are what lasso creates in the `build\static` dir, then there is no `/$/my-components` there, however there is `/node_modules/my-components`

![](http://i.imgur.com/DoaPJXp.png)

is `/$/..` supposed to resolve to `/node_modules/`? Do I need do to something to make that happen?

