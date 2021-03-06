History Utility
===============

Provides browser history management functionality using a simple
add/get/replace paradigm. This can be used to ensure that the browser's back
and forward buttons work as the user expects and to provide bookmarkable
URLs that return the user to the current application state, even in an Ajax
application that doesn't perform full-page refreshes.

The following modules are available:

  * `history`: Rollup of `history-base`, `history-hash`, `history-hash-ie`, and 
    `history-html5`.
  * `history-base`: Generic history management API (but no storage layer).
  * `history-hash`: History management using `window.location.hash`.
  * `history-hash-ie`: Adds IE6/7 back/forward support using an iframe hack.
  * `history-html5`: History management using the HTML5 history API.

When using the `history` rollup module, or when the `history-hash` and
`history-html5` modules are both loaded, `Y.History` will be an alias to the
best adapter supported by the current browser, which may be either
`Y.HistoryHash` or `Y.HistoryHTML5`. Preference is given to `Y.HistoryHTML5` if
the browser supports the HTML5 history API.


Change History
--------------

3.4.0

  * HistoryHTML5 now uses the new `window.history.state` property (which
    showed up in Firefox 4 and the HTML5 spec after YUI 3.3.0 was released) to
    get the current HTML5 history state.
  * Removed the `enableSessionStorage` config option that was previously used to
    work around the lack of an HTML5 API for getting the current state.
  * Bug fix: In IE6 and IE7, navigating to a page with a hash state could result
    in endlessly repeating history:change events. [Ticket #2529990]
  * The `history-deprecated` module, which was deprecated in YUI 3.2.0, has been
    removed from the library.

3.3.0

  * Bug fix: Setting an improperly encoded hash value outside of HistoryHash
    resulted in two history entries being created. [Ticket #2529399]
  * Bug fix: Changes to the URL hash (as opposed to the iframe hash) are now
    reflected in the history state in IE6 and IE7. [Ticket #2529400]

3.2.0

  * Initial release. The pre-3.2.0 Browser History Utility has been
    deprecated.
