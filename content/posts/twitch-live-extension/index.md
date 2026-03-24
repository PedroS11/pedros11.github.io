+++
date = '2026-03-09T17:54:18Z'
draft = false
title = 'Twitch Live Extension'
summary = 'My name is Pedro Silva, and here is everything you need to know about me.'
tags = ["browser-extension", "twitch","chrome", "firefox", "extension", "typescript", "react"]
+++

Twitch Live Extension is a browser extension that will help you find out when your followed streamers are live on Twitch 
and will send notifications when they go live.
 
It's available for Chrome/Edge on the [Chrome Web Store](https://chromewebstore.google.com/detail/twitch-live-extension/nlnfdlcbnpafokhpjfffmoobbejpedgj)
and Firefox on the [Firefox Add-ons](https://addons.mozilla.org/en-US/firefox/addon/twitch-live-extension/).
---
## The idea
Back in 2019, we were all asked to stay at home due to the COVID-19 pandemic. So i ended up spending a lot of time on Twitch and
one day i had an idea to create a simple extension so i could check if my favorite streamers were live.

I never created a browser extension before nor had worked with Twitch API, so it seemed the perfect fit.

## POC

After checking Twtich API documentation, i could check by username, if a streamer was live or not.
So, i used create-react-app to create a simple extension, added jquery + bootstrap, that i knew a bit from university,
hardcoded my favorite streamers and the extension would check their status and display them if live.

<div style="display: flex; gap: 10px; flex-wrap: wrap; align-items: flex-start;">
<img src="1.0.0.png" alt="10x10" title="alt text" style="width: 300px; height: auto;" />
<img src="1.0.0_options.png" alt="img.png" style="width: 300px; height: auto;" />
</div>

Everything was working fine so i uploaded it to Chrome Web Store and Firefox Add-ons and shared it with my friends and 
portuguese streamers that i made friends with.

## [Version 2 - The first major release](https://github.com/PedroS11/twitch-live-extension/pull/6)
This worked pretty well but had a major issue, forced the users to manually input the streamers usernames.
So, I decided to add twitch auth integration so the extension would get all the followers of the account and check if the any of them were live.
The functionality was working perfectly, but the extension wasn't that beautiful. I decided to use add Material UI for the UI
and Redux Toolkit for the state management.

And version 2.0.0 was released! I had back then a few hundred users of it.

<div style="display: flex; gap: 10px; flex-wrap: wrap; align-items: flex-start;">
<img src="2.0.0.png" alt="img.png" style="width: 300px; height: auto;" />
<img src="2.0.0_settings.png" alt="img.png" style="width: 300px; height: auto;" />
</div>

## [Version 2.2 - Add notifications when a streamer goes live](https://github.com/PedroS11/twitch-live-extension/pull/9)

The feedback i got was really good and new features started to get asked. The users wanted to receive a notification
when a streamer went live so i decided to add browser notifications for it.

### The challenge
Twitch API sends notifications when a streamer goes live but you need to subscribe to a webhook and only 3 streamers per account.
Since this was a free extension, I wanted to make it work without any backend because that would add costs to the extension.

So the other option I had was, I have the list of streamers the user follows, if I save them locally,
I can create a polling mechanism that every 3 minutes, it would check if any of them are live. Twitch returns the start stream
timestamp, if they started less than 3 minutes before, that meant it was a new streamer live so i'd send a notification for every new one. 

Browsers have an alarm API so I used it to schedule the polling strategy. I found out while working on this
that I should use a background service worker to deal with the alarms and the flow to fetch the Twitch auth token.
Then, i'd send messages between the background service worker and the popup page and make the code cleaner. This way, 
when the popup was open and there was no token on the local storage, the background script would:
- fetch the token
- send it to the popup page
- popup saves it in local storage
- everytime the popup opens, it fetches from the storage

If the token expired, I had an axios interceptor to refresh the token with a retry policy.

Since not everyone was interested in the went live notifications, I added a toggle in the settings page.

<img src="2.2.0_settings.png" alt="2.2.0_settings.png" style="width: 300px; height: auto;" />
<img src="2.2.0_notification_mac.png" alt="2.2.0_notification_mac.png" style="width: 300px; height: auto;" />

<img src="2.2.0_notification_windows.png" alt="2.2.0_notification_windows.png" style="width: 300px; height: auto;" />

<img src="2.2.0_notification_firefox.png" alt="2.2.0_notification_firefox.png" style="width: 300px; height: auto;" />

## [Version 3 - Twitch API improvemets](https://github.com/PedroS11/twitch-live-extension/pull/12)

Twitch updated their API and added a new endpoint to fetch all live streamers a user follows.
This endpoint would remove the need to save locally the followers and check if any of them were live, one by one.
So, the alarm logic would only call Twitch to get all the live streamers, do the same started at timestamp logic and send notifications.

## [Version 3.1 - Badge icon](https://github.com/PedroS11/twitch-live-extension/pull/13)

I found that every extensio icon can have a smaller badge to display up to 3 characters and 
since I knew how many streamers were live every 3 minutes, I could update the badge with the number of live streamers.
It was some easy but brought a lot of useful information without needing to open the extension.

<img src="3.1.0_badge.png" alt="img.png" style="width: 150px; height: auto;" />

## [Version 3.2 - Elapsed time](https://github.com/PedroS11/twitch-live-extension/pull/18)

I use BetterTTV extension to display some information about the streamer, on their twitch page. One of the things
is how long the streamer was live. Twitch returns the start time of the stream, so i could calculate the elapsed time
since the stream started and display it below the streamer name.

And I also have the stream title, so I'd be useful if, on hover the streamer name, I could see the title of the stream.
So, I released a new version with all theses features.

<img src="3.2.0_elapsed.png" alt="img.png" style="width: 300px; height: auto;" />

## [Version 3.3 - Explore tab](https://github.com/PedroS11/twitch-live-extension/pull/42)

As more feedback was provided in the issues page, I added a new tab on the extension to show the top streamers live on Twitch.
It would fetch the top 10 and with infinite scroll it would load more.

<img src="3.3.0_expore.png" alt="img.png" style="width: 300px; height: auto;" />


## [Version 4.0 - Manifest Version 3 migration](https://github.com/PedroS11/twitch-live-extension/pull/47)

Google Chrome introduced manifest version 3 and gave a deadline to migrate to it otherwise the current extensions would 
not be updated anymore.
So, i took this opportunity to migrate from Redux Toolkit to Zustand, added webpack instead of the create-react-app build.

### Firefox issue
In order to use the extension on Firefox, i was using [webextension-polyfill-ts](https://github.com/Lusito/webextension-polyfill-ts)
to guarantee Chromium and Firefox compatibility.

Starting from version 2.2, the background script would fetch the token and send it to the popup page.
However, the polyfill didn't support manifest version 3 back then, and using Firefox MV3, the comunication between popup and background
was broken, so I couldn't sent the token back. Since I couldn't find a proper fix,
Firefox was left without the new features and stuck on 3.3 for over 3 years until it got fixed recently.

## [Version 4.1 - Search bar on Favorites](https://github.com/PedroS11/twitch-live-extension/pull/55)
Something that never crossed my mind was that some of the users might follow a lot of people and if, even
if a small part of them go live, the Favorites tab will be really long. When I thought about this use case,
I decided to add a search bar on the favorites page.

<img src="4.1.0_search.png" alt="img.png" style="width: 300px; height: auto;" />

## [4.3 - Firefox addon on manifest version 3](https://github.com/PedroS11/twitch-live-extension/pull/80)
After some tiny features were added, in 2026 using AI tools, I was able to change the way Popup/Background comunicated 
to make the token available on the popup. 

I tried multiple ways to make it work, and the final and only solution was to:
- If it's Chrome, leave the communication as it was before:
   - if the token wasn't already saved in the local storage, 
fetch it from the background, return it to the popup via Chrome message API and save it on the local storage.
- If it's Firefox, save the token on the browser storage when the background script runs. Then, everytime the popup is opened, it will fetch the token from the browser storage.


