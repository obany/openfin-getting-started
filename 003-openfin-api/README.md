# 003 - OpenFin API

Now that you have web content in the OpenFin container we can start to use the OpenFin APIs.

Unlike many API models there is no need to rebuild your code or include additional packages to access the APIs. As soon as your content is opened within the OpenFin container the APIs are automatically injected in to the top level `window.fin` object.

A web page can determine if it is running in an OpenFin container by simply performing an `if` check for `window.fin`. This means that you can progressively enhance any of your existing applications.

We have modified our `index.html` to display the OpenFin runtime version if available.

```js
const runtimeElem = document.querySelector('#runtimeVersion');
if (window.fin) {
  runtimeElem.textContent = 'Runtime v' + (await window.fin.System.getVersion());
} else {
  runtimeElem.textContent = 'Runtime version not available.';
}
```

If we open just the web page with <https://start.openfin.solutions/003-openfin-api/> you will see the page says `Runtime version not available`.

But if we run the remote or local examples in the OpenFin container `start fins://start.openfin.solutions/003-openfin-api/manifest.remote.fin.json` or `start fin://localhost:4545/manifest.local.fin.json` we will see something like `Runtime v29.108.73.14` depending on the current stable version of the runtime.

> The second part of OpenFin runtime version e.g. 108 specifies the chromium runtime version the OpenFin runtime is built with, so in the case would have feature parity with Chrome 108.

## Developer Tools

You will find that if you right click in the OpenFin container the context menu will have the `Inspect` menu entry, this allows you to open the Chrome DevTools that you should be familiar with from Chrome.

If you open the `Console` in the DevTools and type `window.fin` you will see all the APIs available to you.

## Process Manager

In addition to the Chrome DevTools we have an additional OpenFin tool `Process Manager`, which allows you to inspect all the OpenFin processes that are running. You can install at the following link <https://start.openfin.co/pm>

:tada: Congratulations you have now used the OpenFin APIs in your application.

---

:arrow_right: Next [004 - ?????](../004-?????/README.md)

## Further Reading

- [Process Manager](https://developers.openfin.co/of-docs/docs/process-manager)
- [Testing and Debugging](https://developers.openfin.co/of-docs/docs/debugging)
