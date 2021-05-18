## Clear a 301 Permanent Redirect

If you accidentally send a 301 permanently moved redirect while developing (possibly redirecting localhost to a live site, or from http to https), you need to clear the cache to fix this issue.

In a chromium browser, (Edge, Google Chrome) the easiest way to do this is as follows:

1. Open a new tab
2. Open the developer tools (CTRL+SHIFT+I) or (F12)
3. Open the Network tab
4. Check the box by "Disable Cache"
5. In the address bar, put the location you need to visit (where you previous sent the 301 from)
6. Visit the site
7. It should load, ignoring the cached 301 response.
