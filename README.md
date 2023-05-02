# dbsaga-mud

The DBSaga MUD Codebase
-----------------------

Dialog about fixing saving player issue (from https://www.reddit.com/r/MUD/comments/132jave/dragonball_saga_online_to_play/ )

deceptively_serious

It appears that if you get to 4k and are able to save, logging out still deletes you anyway. I'd probably remove the auth requirement if you can.

gunfart

this has been fixed, no more auth system!

deceptively_serious

It was fixed but I think reboot may have broke it. i think you maybe need to cset save to get it to stick?

gunfart

i've been playing it all night and haven't had any problems. my character is saved and another player has been playing off and on as well.
regardless, i saved settings just in case. hope this resolves any lingering issues. if not, i am open to suggestions.

thanks!

deceptively_serious

so once you're auth'd your fine it looks like. but when your automatic reboot happen it appears it cleared out the cset auth setting,
if it wasn't saved then when the reboot happens it'll go back i believe. i was playing fine before too but I just made another alt and its giving me
the auth message still

so you probably need to cset auth, cset save one more time i think?

gunfart

done
