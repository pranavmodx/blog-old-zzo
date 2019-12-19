+++
author = "Pranav Shridhar"
title = "Python Script : Despotify"
date = "2019-05-11"
description = "Muting annoying Spotify advertisements"
tags = [
    "python",
    "script",
]
categories = [
    "tech"
]
+++

Hey yo! If you are one of those people who recently got to know about Spotify after their much hyped release in India, then you’re not alone. I immediately switched from Youtube (yeah that :) ) to Spotify after I heard that their song recommendations were very good.

Little did I know that they had very annoying audio ads glued after *each* song. After few days of patien
tly listening to these, I decided it was high time to do something about it or I would get interrupted constantly in my work.

I wrote a small Python script using Al Sweigart’s [pyAutoGUI](https://pyautogui.readthedocs.io/en/latest/) module, a cross-platform GUI automation for “human beings” (as given in their docs :D). It was indeed fun writing it. The joy of writing programs which actually find a proper use is very satisfying. Well, enough said. Let’s take a look at the code.

![](https://cdn-images-1.medium.com/max/2000/1*nxgK3JNlRXjLOZQVRImoEQ.png)

The first step is to ensure Spotify is open and active on the screen. This enables pyAutoGUI to locate stuff on the app.

![](https://cdn-images-1.medium.com/max/2000/1*2XYjWASjkO0GgKnvNF4jVw.png)

Second is to identify when an ad is playing. I did this by taking screenshots of the ad’s duration.

By searching for the exact same duration count in the current instance of the app, we can easily distinguish an ad from an actual song.

Accordingly, we can mute or unmute the speaker for the required time. The speaker button is located in a similar manner and a mouse click is performed if it is found within the full range of the screen.

That’s it! As simple as that. Now every time an ad plays, just run the script and you’re good to go. It’ll do the rest for you. Sure there are many limitations to this, but I guess this will do it for now.

Python is love. The code is available in my [github](https://github.com/pranavmodx/pyAutomate) repo.

Thanks for reading.