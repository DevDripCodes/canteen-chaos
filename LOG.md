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

## CC-04 — "Add to cart does not work on tablets "

**Reproduced:** In the dev tools I changed the width to about 761px and the problem appeared that add to cart buttons are not working also the favorite star icon is not working too.

**Cause:** This is due to a Pseudo element :active which is in CSS file with media query for tablets in line 1042 and 1043 the main issue was 2 pseudo elements were placed.

**Fix:** I deleted all the lines that creates Pseudo elements

**Checked:** The buttons work in all screen sizes.

**Time:** About 20 mins

## CC-05 — "The filters tab was scrolling away"

**Reproduced:** I checked the site and found it was scrolling away not only in mobile but in every screen size.

**Cause:** This is caused due to top=0 in .filters since header is also top 0 hence the filters scroll away.

**Fix:** I changed top to 91.5px the total size of header and changed overflow-x to clip in mobile optimizations

**Checked:** The filters stays on each screen size.

**Time:** About 20 mins


## CC-06 — "I ordered more than they had"

**Reproduced:** The order validation only rejected a dish when its stock was zero, so an order quantity larger than the available stock could get through that check.

**Cause:** `reserveStock` subtracted the requested quantity without checking whether enough stock was available.

**Fix:** I added a stock check in `reserveStock` before subtracting the quantity, so it can reject an order when the requested amount is greater than the remaining stock.

**Checked:** Verified that orders above available stock are rejected.

**Time:** 10 mins

## CC-07 — "Cancelling makes it worse"

**Reproduced:** When an order was cancelled, the stock count for the ordered dish went down instead of going back up.

**Cause:** `releaseStock` subtracted the cancelled quantity from the menu stock.

**Fix:** I changed `releaseStock` to add the cancelled quantity back to stock.

**Checked:** Verified that cancelled quantities are returned to stock.

**Time:** 5 mins

## CC-08 — "An old coupon still works"

**Reproduced:** The expired `FRESHERS24` coupon was still accepted when pricing an order.

**Cause:** `applyCoupon` checked coupon usage and order conditions, but did not reject coupons past their expiry date.

**Fix:** I added an expiry check to `applyCoupon` so an expired coupon returns an error and no discount.

**Checked:** Verified that expired coupons are rejected and unexpired coupons remain valid.

**Time:** 25 mins

## CC-09 — "The menu shows more dishes than it should"

**Reproduced:** The menu request asked for five dishes per page, but the response returned the full dish list.

**Cause:** `paginate` calculated the page slice but returned the original full list in its `items` field.

**Fix:** I changed `paginate` to return the calculated `items` slice, so each response contains only the requested page.

**Checked:** Verified that pagination returns only the requested page.

**Time:** 30 mins

## CC-10 — "Sorting by price is backwards"

**Reproduced:** Selecting “Price: low to high” put the expensive dishes first, and “Price: high to low” put the cheaper dishes first.

**Cause:** The price sort comparators were reversed in `SORTERS`.

**Fix:** I swapped the comparator directions for `price-asc` and `price-desc`.

**Checked:** Verified that both price sort directions work correctly.

**Time:** 10 mins


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
