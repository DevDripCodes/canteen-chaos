# Debug log

Your notes. One entry per bug you fixed, using the template below.

This file is read as carefully as your code. A correct fix you cannot
explain counts for little; a bug you could not fix but investigated
honestly still counts for something.

Delete the example before you submit.


## CC-01 — "Search box behind everything"

**Reproduced:** When typing anything on the search box the suggestions were behind the category tabs.

**Cause:** when using dev tools I found that it was a layering problem due to incorrect z-index.

**Fix:** changed the z-index to 100 that is much higher than other components

**Checked:** Search suggestions are now showing properly

**Time:** About 10 mins

## CC-02 — "Hard coded color in dark mode"

**Reproduced:** When running the site in dark mode the color of text should change but it didn't.

**Cause:** I first checked the color scheme in css file it was correct other colors were changed so only one component the text was not changing.

**Fix:** I found the id using dev tools and found that the color was hardcoded instead of using -varInk fixed it.

**Checked:** all the colors are showing according to the color scheme.

**Time:** About 20 mins

## CC-03 — "Mobile screen menu card clipping"

**Reproduced:** In the dev tools I changed the width to about 600px and the problem appeared the right column of the menu grid does not shrink.

**Cause:** I checked the responsive part in the css file for screens less than 760px wide the properties for .dish-card img is wrong they used width auto and min-width 100% this meant the image cannot shrink and the card was overflow:clip so the box changed the size according to image.

**Fix:** removed .name-btn { width: max-content; } and changed width to 100% this meant it will take size according to 2,1 grid

**Checked:** The layout is now proper in each screen size.

**Time:** About 20 mins

## Could not fix

For anything you investigated but did not solve. Say what you tried and
where you got to. This is worth marks — leaving it blank when you got
stuck is not.

### CC-0X — "<the complaint>"

**What I tried:**

**Where I got to:**

**What I would try next:**



## Extra credit

Anything not on the bug log: a problem you found yourself, a test you
wrote, or a fix you are unsure about. Same format, plus one line on how
you noticed it.
