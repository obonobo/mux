# obonobo/mux

Tweaked version of [gorilla/mux](https://github.com/gorilla/mux)

The tweaks are as follows:

1. `Router.StrictSlash` now _enables_ strict slash functionality, rather than
   disabling strict slashes like it does in `gorilla/mux`. I'm not sure why it
   was coded that way in the first place.

2. `Router.StrictSlash` is now disabled by default, so by default `/some/path/`
   matches the same as `/some/path`. Again, this really should be the default
   behaviour - you should need to _enable_ strict slashes to get that behaviour.

3. `Router.StrictSlash` no longer redirects. For reference, the default
   behaviour in `gorilla/mux` is that when you enable `StrictSlash` and register
   a route like `/some/path`, a request to `/some/path/` will _redirect_ (301
   Moved Permanently) to `/some/path`. Why? I have no clue. This fork changes
   this behaviour so that, instead of redirecting, both routes are simply
   matched equally. If you register `/some/path`, requests made to _either_
   `/some/path` or to `/some/path/` will match against the same handler.
