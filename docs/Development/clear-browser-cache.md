## About Redirect Caching

**In the absense of cache control directives that specify otherwise, a 301 redirect defaults to being cached without any expiry date.**

That is, it will remain cached for as long as the browser's cache can accommodate it. It will be removed from the cache if you manually clear the cache, or if the cache entries are purged to make room for new ones.

You can verify this at least in Firefox by going to about:cache and finding it under disk cache. It works this way in other browsers including Chrome and the Chromium based Edge, though they don't have an about:cache for inspecting the cache.

In all browsers it is still possible to override this default behavior using caching directives, as described below:

### If you don't want the redirect to be cached

This indefinite caching is only the default caching by these browsers in the absence of headers that specify otherwise. The logic is that you are specifying a "permanent" redirect and not giving them any other caching instructions, so they'll treat it as if you wanted it indefinitely cached.

The browsers still honor the Cache-Control and Expires headers like with any other response, if they are specified.

You can add headers such as Cache-Control: max-age=3600 or Expires: Thu, 01 Dec 2014 16:00:00 GMT to your 301 redirects. You could even add Cache-Control: no-cache so it won't be cached permanently by the browser or Cache-Control: no-store so it can't even be stored in temporary storage by the browser.

Though, if you don't want your redirect to be permanent, it may be a better option to use a 302 or 307 redirect. Issuing a 301 redirect but marking it as non-cacheable is going against the spirit of what a 301 redirect is for, even though it is technically valid. YMMV, and you may find edge cases where it makes sense for a "permanent" redirect to have a time limit. Note that 302 and 307 redirects aren't cached by default by browsers.

### If you previously issued a 301 redirect but want to un-do that

If people still have the cached 301 redirect in their browser they will continue to be taken to the target page regardless of whether the source page still has the redirect in place. Your options for fixing this include:

A simple solution is to issue another redirect back again.

If the browser is directed back to a same URL a second time during a redirect, it should fetch it from the origin again instead of redirecting again from cache, in an attempt to avoid a redirect loop. Comments on this answer indicate this now works in all major browsers - but there may be some minor browsers where it doesn't.

If you don't have control over the site where the previous redirect target went to, then you are out of luck. Try and beg the site owner to redirect back to you.

Prevention is better than cure - avoid a 301 redirect if you are not sure you want to permanently de-commission the old URL.

_Source: [Thomas Rutter - Stack Overflow answer](https://stackoverflow.com/a/21396547)_

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
