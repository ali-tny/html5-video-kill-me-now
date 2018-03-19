html5-video-kill-me-now
=======================
A minimal example of a frustrating bug ~~I haven't managed to fix~~\* with
getting HTML5 videos to masquerade as gifs in Safari. Loading HTML5 videos via
jQuery in Safari results in a strange bug where the video won't display until
the tab is hidden and reopened.

\* Hacky fix in branch `hacky-workaround`. See details below

To run (with python 3):
- run `make run`
- go to [http://localhost:8001/1.html](http://localhost:8001/1.html) in Safari
- scroll down
- open a new tab then go back to the original
- pull hair out

Workaround
----------
After much exploration, it seems that Safari doesn't like loading HTML video via
`jQuery.load()` if you give it a selector. I assume this is what is happening
behind the scenes in `infinite-scroll`, since you have to give it the div class 
that it uses to update the container. Safari will happily load the videos via
jQuery if you let it load the whole page, so the workaround has skeleton
pages for the extra content that gets loaded in full (taking advantage of the
`infinite-scroll` library via a custom load method).
