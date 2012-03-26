# Miami 2012 UHack

5 live demos in 5 minutes, powered by the [Hunch API][1]. 5x the danger, 10x the network bandwidth...

**TL;DR Check out the [Hunch API reference][2].**

# Demos

## [Fast Forward][3]

  * Discover New Music for Old-Schoolers
  * API calls used

    * [get-results][4] (search for an artist with a given name)
    * [get-recommendations][5] (get artist recommendations for a person that likes that artist)

## [Popcorn][6]

  * Adds Hunch recommendations to Google's Movie Showtimes pages
  * API calls used

    * [get-recommendations][7]

  * Protip: result_ids can be from:

    * Amazon (amz_)
    * Facebook (fb_)
    * Foursquare (4sq_)
    * Hunch (hn_)
    * IMDB (imdb_)
    * Musicbrainz (mb_)
    * Spotify (sp_)
    * TripAdvisor (tp_)
    * Twitter (tw_)
    * Yelp (yelp_)

## [Restaurantology][8]

  * I'm homesick for _that restaurant I used to love back in High School_ but I live in _Juneau, Alaska_.
  * API calls used

    * [get-results](http://api.hunch.com/api/v1/get-results?query=five%20guys&topic_ids=list_restaurant&minimal=1) (find the restaurant in your hometown)
    * [get-similar-results][9] (find similar restaurants in your current location)

## [Brdg.me][10]

  * Find awesome people nearby
  * API calls used

    * [get-tastemates][11] (find the user with fashion sense most like Twitter user "gleitz")
    * [get-recommendations][7] (find movies that person likes, to use as an icebreaker)

## [AutomaticDJ][12]

  * Build custom music playlists using facial recognition
  * Leverages the [Face.com][13] API as well as [Echo Nest][14]
  * API calls used

    * [get-recommendations][15]

## BONUS: [Hunch.fm](http://hunch.com/fm/)

  * Personalized, streaming music a la pandora
  * API calls used

    * [get-recommendations][15]

## BONUS: [Hunch Movies](http://hunch.com/movies/)

  * Better-than-Netflix movie recommendations
  * API calls used

    * [get-recommendations][15]

## BONUS: [Spotify Playlist Generator][16]

  * Generate bumpin' playlists for all your groovy friends
  * API calls used

    * [get-recommendations][15]

## BONUS: [Hunch Movie Map][17]

  * Find what movies connect you and your friends
  * (Log in with your Hunch.com username and password)
  * API calls used

    * [batch][18] (allows you to execute multiple API request in one call. very snazzy)

              http://api.hunch.com/api/v1/batch/?auth_basic=1&calls=


				  [
					{"name":"get-recommendations",
					 "params":
						{"friend_id":"tw_gleitz",
						 "limit":"10",
						 "topic_ids":"list_movie"}},
					{"name":"get-recommendations",
					 "params":
						{"_result_ids":"responses[0].recommendations.result_id",
						 "minimal":true,
						 "limit":10,
						 "popularity":".1",
						 "friend_id":"tw_pennapps"},
					 "requires":["responses[0].recommendations.result_id"]}
				  ]

## What Should I Build??
* Group recommendations
  * I'm going to dinner with Wesley Snpes, Kenny G., and Staff Sergeant Max Fightmaster. Where should we go? Check out the [group recommendations][23] call.

* A browser extension that takes the current page you are on (Amazon, Facebook, Yelp) and shows your affinity to that page.

* Generate a Tumblr blog on the fly that pulls down interesting Hunch results. People could follow it and the recommendations would evolve based on the followers.

* A Foursquare hack that pulls down all the places you've been and recommends similar spots, similar items, or similar people.

* A "stereotype generator" that shows things that people like that frequent particular Foursquare places (Cufflinks and golf clubs for the Four Seasons, Birkenstocks and anti-nuclear proliferation for Whole Foods).

* A turntable.fm mashup that recommends rooms based on your similarity to people in the room.

* A clone of [EchoFi](http://echofiapp.com/), powered by Hunch.

## Links Worth Reading

  * [Hunch API][1]
  * [Hunch API reference][2]
  * [Hunch Topics][19]
  * [Code Samples][20]
  * [API Console][21]
  * [Introduction to Google App Engine by Guido van Rossum][22]

**Good luck! Go out there and crunch some data!**

   [1]: http://hunch.com/developers/
   [2]: http://hunch.com/developers/v1/docs/reference/
   [3]: http://labs.gleitzman.com/music/
   [4]: http://api.hunch.com/api/v1/get-results?query=metallica&topic_ids=list_musician&minimal=1
   [5]: http://api.hunch.com/api/v1/get-recommendations?likes=hn_3570964&topic_ids=list_musician&blocked_result_ids=hn_3570964
   [6]: https://github.com/workmajj/popcorn
   [7]: http://api.hunch.com/api/v1/get-recommendations/?auth_basic=1&result_ids=imdb_tt0110357
   [8]: http://www.metarade.com/restaurantology/
   [9]: http://api.hunch.com/api/v1/get-similar-results/?topic_ids=list_restaurant&minlat=39.815&maxlat=40.089&minlng=-75.419&maxlng=-74.907&limit=10&result_id=hn_3718054&tags=burgers
   [10]: http://brdg.me/
   [11]: http://api.hunch.com/api/v1/get-tastemates/?topic_ids=cat_fashion&user_id=tw_gleitz&user_ids=tw_oprah,hn_katygleitz,tw_pennapps,fb_GlennBeck
   [12]: https://github.com/gleitz/automaticdj
   [13]: http://http://face.com/
   [14]: http://developer.echonest.com/
   [15]: http://api.hunch.com/api/v1/get-recommendations/?topic_ids=list_musician&sites=sp&auth_basic=1
   [16]: http://hunch.com/apps/spotifydemo/
   [17]: http://labs.gleitzman.com/map/
   [18]: http://api.hunch.com/api/v1/batch/?calls=[{%22name%22%3A%22get-recommendations%22%2C%22params%22%3A{%22friend_id%22%3A%22tw_gleitz%22%2C%22limit%22%3A%2210%22%2C%22topic_ids%22%3A%22list_movie%22}}%2C{%22name%22%3A%22get-recommendations%22%2C%22params%22%3A{%22_result_ids%22%3A%22responses[0].recommendations.result_id%22%2C%22minimal%22%3Atrue%2C%22limit%22%3A10%2C%22popularity%22%3A%22.1%22%2C%22friend_id%22%3A%22tw_pennapps%22}%2C%22requires%22%3A[%22responses[0].recommendations.result_id%22]}]
   [19]: http://hunch.com/developers/v1/topics/
   [20]: http://hunch.com/developers/v1/resources/samples/
   [21]: http://hunch.com/developers/v1/resources/console/
   [22]: http://www.stanford.edu/class/ee380/Abstracts/081105.html
   [23]: http://api.hunch.com/api/v1/get-recommendations/?topic_ids=list_movie&group_user_ids=tw_17289881,tw_173940470
