# PennApps 2011 Hackstravaganze

5 live demos in 5 minutes, powered by the [Hunch API][1] 5x the danger, 10x
the ACKs.

**TL;DR Check out the [Hunch API reference][2].**

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

  * I'm homesick for "..." but I live in "..."
  * API calls used

    * [get-results][4] (search for an artist with a given name)
    * [get-similar-results][9]

## [Brdg.me][10]

  * Find awesome people nearby
  * API calls used

    * [get-tastemates][11] (find the user with fashion sense most like Twitter user "gleitz")
    * [get-recommendations][7]

## [AutomaticDJ][12]

  * Build custom music playlists using facial recognition
  * Leverages the [Face.com][13] API as well as [Echo Nest][14]
  * API calls used

    * [get-recommendations][15]

## BONUS: [Spotify Playlist Generator][16]

  * Generate bumpin' playlists for all your groovy friends
  * API calls used

    * [get-recommendations][15]

## BONUS: [Hunch Movie Map][17]

  * Find what movies connect you and your friends
  * (Log in with you Hunch.com username and password)
  * API calls used

    * [batch][18] (allows you to execute multiple API request in one call)

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
			 "requires":["responses[0].recommendations.result_id"]}]

## What Should I Build??

## Links Worth Reading

  * [Hunch API][1]
  * [Hunch API reference][2]
  * [Hunch Topics][19]
  * [Code Samples][20]
  * [API Console][21]
  * [Introduction to Google App Engine by Guido van Rossum][22]

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