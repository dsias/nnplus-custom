nnplus-custom
=============

My Modifications to Newznab+
----------------------------
I base my modifications on the on the theory that the changes to feel like they were always there all along. 
This tends to steer me into asthetic and functional changes in the front end interface currently. 
I have made some small adjustments that would go good with most layouts and themes and that is what I was going for. 


MOVIES COVER PAGE:
This change drove me nuts in the absense and incomplete feeling everytime I saw it. 
In Cover view on the movies page if you click on the poster you are given a modal that is made using a fanart from the movie, the movie poster, and Title, Year, Overview. 
This works great IF there is the poster and backdrop, otherwise its a gray bland empty feeling. So I made a new image. 
Found a good generic movie theme image, cropped it, added a blur and darkened it and I create.

no-backdrop.jpg -  (dimensions 1024x576 if you want to make your own)

This file will go into newznab/www/covers/movies.
Also, not that Im not a fan of the No cover, but I made my own as well.

no-cover.jpg - replaces the one that is already in newznab/www/covers/movies.

To make the background work I updated this file. newznab/www/views/templates/viewmovie.tpl
I updated line 5ish to this:

{if $movie.backdrop == 1}<div id="backdrop"><img src="{$smarty.const.WWW_TOP}/covers/movies/{$movie.imdbID}-backdrop.jpg" alt="" /></div>
{else}<div id="backdrop"><img src="{$smarty.const.WWW_TOP}/covers/movies/no-backdrop.jpg" alt="" /></div>{/if}


Attached the files if you just want to drag and drop replace. 




BROWSE RELEASES - NOW WITH PREVIEWS   http://imgur.com/a/rIq4U#0
-----------------------------------

NOTE: THIS IS NOT THE TVRAGE POSTERS IN THE SERIES PAGE. THESE ARE THE PREVIEW THAT GETS GENERATED VIA FFMPEG FOR THAT SPECIFIC RELEASE.
AND ... Working on adjusting it to not show if no previews on the page. But I get disctracted with so many ideas for the site. 

The browse page now has a new column that shows the preview image in thumbnail format that you can click for the larger modal (the same preview as the little button next to NFO and View Series under the Release Names). Works on list views for TV and Movies as FFMPEG with attempt to generate for both. Working on adjusting it to not show if no previews on the page or tweak it to fit the other releases. But I get disctracted with so many ideas for the site. 

VIEW SERIES - WITHOUT ALL THE WASTED SPACE
------------------------------------------
I felt the view series was not layed out the best and honestly the movies side had the right idea. So I started altering my tpl file to match. I made the image fixed in poster size however this does not go well with TVRAGE scrapped images. I would like to work with someone that knows php/sql and the back end of the site (Lib folder) to see about, at least, adding the banners.xml to thetvdb api that gets performed. 

This would give us nicer uniformed Poster, Banner, and Fanart image for each tv sieries (not looking to so the season, just the main Series Images) If I can get that. I have two layout ideas for the Series page. The one I have now and the other using the Banner at the top with the title instead of the poster, and using the poster in a NEW SERIES Cover view page like the rest. (basically would be an update to the Series list page)

For the SERIES and BROWSE I have added the tpl files for drag and drop install. 
These files replace the files at newznab/www/view/templates/frontend/ 

You need to have ffmpeg working and previews available to you or else you get empty column. 
(future plan to have profile checkbox to enable/disable previews in list view)



WHAT I WOULD REALLY LIKE.... If I can learn the lib/php/sql or have some help. I would love to be able to detach the TVRAGE from the show releases as a dependancy, this setup causes issues with being able to update releases when you manually set the rageid, and kills the ability to further post process tvdb and anidb if you turn off tvrage. 