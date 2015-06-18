Atomic Plugins for Game Center
========================================

This repo contains Cocoon Social Interface for the Game Center Extension designed using the [Atomic Plugins paradigm](#about-atomic-plugins). 

You can contribute and help to create more awesome plugins.

##About Atomic Plugins

Atomic Plugins provide an elegant and minimalist API and are designed with portability in mind from the beginning. Framework dependencies are avoided by design so the plugins can run on any platform and can be integrated with any app framework or game engine. 

#Provided APIs

  * [JavaScript API](#javascript-api)
  * [API Reference](#api-reference)
  * [Introduction](#introduction)
  * [Setup your project](#setup-your-project)
  * [Example](#example-1)

##JavaScript API:

###API Reference

See [API Documentation](http://ludei.github.io/cocoon-common/dist/doc/js/Cocoon.Social.GameCenter.html)

###Introduction 

Cocoon.Social.GameCenter class provides an easy to use social interface for GameCenter. 

###Setup your project

Releases are deployed to Cordova Plugin Registry. You only have to install the desired plugins using Cordova CLI, CocoonJS CLI or Ludei's Cocoon.io Cloud Server.

    cordova plugin add com.ludei.social.ios.gamecenter;

The following JavaScript file is included automatically:

[`cocoon_social.js`](https://github.com/ludei/atomic-plugins-social/blob/master/src/js/cocoon_social.js)
[`cocoon_gamecenter.js`](src/js/cocoon_gamecenter.js)

###Example

	var social;

	if (Cocoon.getPlatform() === 'ios') {
		
		social = Cocoon.Social.GameCenter.init();
		social = Cocoon.Social.GameCenter.getSocialInterface();
	
		var loggedIn = social.isLoggedIn();

		function loginSocial() {
		  if (!social.isLoggedIn()) {
		      social.login(function(loggedIn, error) {
		           if (error) {
		              console.error("login error: " + error.message);
		           }
		           else if (loggedIn) {
		              console.log("login succeeded");
		           }
		           else {
		              console.log("login cancelled");
		           }
		      });
		  }
		}

		loginSocial();

	    social.submitAchievement(achievementID, function(error){
	    	if (error)
	        	console.error("submitAchievement error: " + error.message);
		});

		social.showAchievements(function(error){
	    	if (error)
	        	console.error("showAchievements error: " + error.message);
		});

		social.submitScore( score, function(error){
    		if (error)
        		console.error("submitScore error: " + error.message);
		});

		social.showLeaderboard(function(error){
   			if (error)
     			console.error("showLeaderbord error: " + error.message);
		});

	    social.logout();
	}

#License

Mozilla Public License, version 2.0

Copyright (c) 2015 Ludei 

See [`MPL 2.0 License`](LICENSE)