# cronux

Flux-based routing. No more data dependency nonsense!

s2u (state to url) for app behavior:
- dispatch action (change_hash_to_x)
- stores process action
- compile state into hash
- set hash
- inhibit listener for next hashchange

u2s (url to state) for clicked links or page visits:
- hashchange fired (doesn't fire when hash is set but doesn't change)
	- onload as well if page was loaded with hash
- destructure url into url object (hash.split(/\//)? some parsing lib?)
- submit change as action, url object as data
- each store processes url object
- call component listeners

s2u and u2s are not transitive, but the idea is that u2s should overwrite relevant properties of the state and leave the rest, whether they are preexisting or default properties.

Putting routing into flux should improve speed and make your actual routing clearer.
