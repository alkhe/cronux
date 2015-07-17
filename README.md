# cronux

Flux-based routing. No more data dependency silliness!

s2u (state to url):
- action to change hash submitted
- stores have processed action
- get state
- derive state into hash
- set hash and inhibit listener for next hashchange

u2s (url to state):
- hashchange (doesn't fire when hash is set but doesn't change)
	- onload as well if page was loaded with hash
- destructure url into url object (hash.split(/\//)? some parsing lib?)
- submit change as action, url object as data
- each store processes url object
- call component listeners

s2u and u2s are not transitive, but the idea is that u2s should overwrite relevant properties of the state and leave the rest, whether they are preexistent or default.

Putting routing into flux should improve speed and make things clearer.
