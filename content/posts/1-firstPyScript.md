+++
author = "Pranav Shridhar"
title = "First Python Script"
date = "2018-08-29"
description = "Converting a disorganized text file into a neat CSV file"
tags = [
    "python",
    "script",
]
categories = [
    "tech"
]
+++

So I decided to learn Python. Turns out this computer programming language isn’t so hard (well, until I got this project! :P ).

Within seconds, I fell in love with its easy, crisp syntax and its automatic indentation while writing. I was mesmerized when I learned that data structures like lists, tuples and dictionary could be created and initialized dynamically with a single line (like so, list-name = [] ).

Moreover, the values held in these could be accessed with and without the use of indexes. This makes the code highly readable as the index is replaced by an English word of one’s choice.

Well, enough said about the language. Let me show you what the project demanded.

My brother gave me this project. He came across a text file containing thousands of words. Many of the words shared almost the same meaning. Each word had its definition and an example sentence next to it but in a not-so-organized manner. There were spaces and newlines between a word and its sentence. Some aspects were missing from the words. Below are the snippets of the text file which I’m talking about:

![Here, ‘Glower’ is preceded by a newline whereas others are not](https://cdn-images-1.medium.com/max/2000/1*C8zDYnZVHBPcnHcUdvY0BA.png)*Here, ‘Glower’ is preceded by a newline whereas others are not*

![Here, the example of ‘Shirk’ is preceded by a newline](https://cdn-images-1.medium.com/max/2000/1*cwfRkxNHoyIS_c9AZiERMw.png)*Here, the example of ‘Shirk’ is preceded by a newline*

He wanted the text aspects to be uniform. For that, he needed me to neatly assort all similar meaning words beside a topic. He told me that this could be achieved by capturing all the data in the text into a dictionary in the following format:

![‘Topic’ is the key and the rest are the key’s value. The format gets slightly trickier to maintain as each topic contains multiple words](https://cdn-images-1.medium.com/max/2000/1*JfdONPyaCI8QJOIdUQXclw.png)*‘Topic’ is the key and the rest are the key’s value. The format gets slightly trickier to maintain as each topic contains multiple words*

and then writing them into a CSV (Comma Separated Values) File.

He asked if I could take this up as my first project, now that I had learned the fundamentals. I was thrilled to work out the logic and so I instantly agreed. When asked about the deadline, he gave me a decent time of 2 days to finish.

Alas, I ended up taking double amount of time for I struggled to debug the written code properly. Frankly, if it hadn’t been for my brother’s short visits to my room to look at the progress and hinting at the wrong assumptions made by me while writing the conditions, I was destined to finish the project in eternity :P

I began by creating mini tasks within the program which I sought to finish before building up the entire program. These were as listed below:

### 1. Forming a Regex to match a number and the word next to it.

I examined the text file and noticed that every topic (herein referred to as ‘key’ ) had a number preceding it. So, I wrote a few lines of code for making a regex (regular expression — a powerful tool to extract text) of the pattern as follows:

![The above code finds matches as per the regex and adds it to a list of strings.](https://cdn-images-1.medium.com/max/2000/1*UBHX1S9kRf1vA9ulyUqSIw.png)*The above code finds matches as per the regex and adds it to a list of strings.*

However, when I ran this I got an error, UnicodeDecodeError, to be exact which meant I didn’t have access to the text file. I looked it up in [https://stackoverflow.com](https://stackoverflow.com) and after a long search with no luck, my brother came and found a solution. The error was rectified as follows:

![Funny, how a single line — “errors = ‘replace’ ” did the job](https://cdn-images-1.medium.com/max/2000/1*c3o7Kgk_b7YFap_8xbqBkg.png)*Funny, how a single line — “errors = ‘replace’ ” did the job*

Still, I didn’t get the desired output. This was because some keys had slashes (‘/’) or spaces (‘ ‘) in the text which my regex couldn’t match. I thought of improving the regex expression later and so wrote a comment next to it.

### 2. Obtaining a list of lines as strings from the text file

For this, I wrote just 1 line of code and fortunately, no errors showed up.

![Sometimes, all you need is 1 line of code!](https://cdn-images-1.medium.com/max/2000/1*t9-7X47DZbRX27x-pNH3Ng.png)*Sometimes, all you need is 1 line of code!*

However, I obtained an unclean list. It contained newlines (‘\n’) and spaces (‘ ‘) I then sought to refine the list as follows:

![First ‘for’ loop replace ‘\n’ with ‘’ and the second one deletes ‘’, thus giving a clean list.](https://cdn-images-1.medium.com/max/2000/1*07LvlZeJvpvxq8OzI-39qw.png)*First ‘for’ loop replace ‘\n’ with ‘’ and the second one deletes ‘’, thus giving a clean list.*

### 3. Extracting words, meanings, and example sentences separately and adding them to corresponding lists.

This was by far the hardest part to do as it involved proper logic and proper judgment by pattern recognition.

Interestingly, while glancing over the text file, I noticed more patterns. Every word had its meaning in the same line separated by a ‘=’ sign. Also, every example was preceded by ‘:’ sign and ‘Example’ keyword.

I thought of making use of regex again. I found an alternate and more elegant solution by slicing the line (now a string in the list) according to the placement of the symbols. Slicing is another cool feature in python. I wrote the code as follows:

![Slicing collects two indexes and extracts the string between them](https://cdn-images-1.medium.com/max/2000/1*yQBEgI5FgvC4Sr2gBR9MTQ.png)*Slicing collects two indexes and extracts the string between them*

The above code reads almost like English. For every line in the clean list, it checks whether it has a ‘=’ or a ‘:’ sign. If it does, then the index of the sign is found and slicing is done accordingly.

In the first ‘if’, the part before the ‘=’ is stored in the variable ‘word’ and the part after it is stored in ‘meaning’. Similarly for the second ‘if’ (‘elif — else if — in this case), the part after ‘:’ is stored in ‘example’. And after each iteration, the word, meaning and example sentence are stored in the corresponding lists. In this way, the whole data can be extracted.

So far so good. But, I noted that the extraction was to be done in a manner such that every word (and its aspects) of the particular key had to be accumulated together as one value for the key. This meant it was required to store each word, meaning, and example inside a tuple. Each tuple was to be stored inside a single list which would represent itself as the value for a particular key. This is depicted below:

![The format for storing all data as one single value for a particular key](https://cdn-images-1.medium.com/max/2000/1*3nFFY4GEnA6e6jJRde1bFQ.png)*The format for storing all data as one single value for a particular key*

For this, I planned to collect each word, meaning and sentence of each key inside a separate list enclosed by another list, say key-list. Again, the picture will tell you more precisely:

![A separate list of words for each key and similarly for meanings and examples](https://cdn-images-1.medium.com/max/2000/1*NP79b1Brp5juWqV3_LDnZQ.png)*A separate list of words for each key and similarly for meanings and examples*

To do this, I added the following code to the one which I wrote for slicing:

![Doing the right things isn’t always easy and what looks easy isn’t always right!](https://cdn-images-1.medium.com/max/2000/1*0hzUVVPr_g4m_QDLI3uRlw.png)*Doing the right things isn’t always easy and what looks easy isn’t always right!*

This code’s logic (the else part) turned out to be wrong, unfortunately. I wrongly assumed that only 2 conditions(‘=’ and ‘:’) existed in the text. There were many exceptions which I failed to notice. I ended up wasting hours for debugging possible errors in the logic. I had assumed that the complete text file followed the same pattern. But that was simply not the case.

Unable to make progress, I moved on to the next part of the program. I thought I could use some help from my brother after completing the other parts. :P
> To be continued…

### 4. Creating values for keys using Zip Function and Parameter Unpacking.

At this point, I wasn’t entirely sure what I would do even after achieving the above configuration of lists. I had learned about ‘Zip’ function and ‘Parameter Unpacking’ during one of my brother’s tech talks, which literally zipped the lists passed to it, like so:

![Zip Function in Python](https://cdn-images-1.medium.com/max/2000/1*_r_64RQH5ke5BDaef-9Ing.png)*Zip Function in Python*

So I thought I could somehow combine those two features to achieve the desired result. After a bit of to-ing and fro-ing, testing the features and working on dummy lists, I succeeded. I created a separate file (beta) for this task, the snippet of which is given below:

![This fragment of code worked flawlessly! :)](https://cdn-images-1.medium.com/max/2000/1*oBz7RuxS3_roeS6j2F8woA.png)*This fragment of code worked flawlessly! :)*

The working of the above code can be figured out by having a look at the output:

![List5 is the required final output](https://cdn-images-1.medium.com/max/2000/1*EZ8JsUoOvVd00DJ11KnsfA.png)*List5 is the required final output*

The zip() function zips the corresponding lists or values within the lists and encloses them in a tuple. The tuples inside the lists are then converted to lists for unpacking and further zipping. Finally, the desired output is obtained.

I felt much relieved for the code worked this time. I was happy that I could manipulate the would-be extracted data and mold it into the required format. I copied the code to the main file on which I was working and modified the variable names accordingly. Now all there was left to do was to assign values to the keys in the dictionary (and of course the extraction part!).

### 5. Assigning values to the keys in the dictionary.

For this, I came to this solution after some experimentation with the code:

![](https://cdn-images-1.medium.com/max/2000/1*pYxm7mphJQFSyFBUrUPnPg.png)

This produced the desired output as follows:

![This output is based on the beta file containing both prior and current fragments of code.](https://cdn-images-1.medium.com/max/2000/1*O4z_-Mx-X1Yu1-1dDKIpMg.png)*This output is based on the beta file containing both prior and current fragments of code.*

The program was almost done. The main problem lay in the data extraction part.
> … continuation from section 3

After hours and hours of debugging, I grew more and more frustrated as to why the damn thing didn’t work. I called my brother and he gave me a subtle hint about the assumptions I had made while defining the conditional loops and if-else clauses. We scrutinized the text file and noticed that some words had examples in two lines instead of one.

![Here, the example sentences for ‘Incense’ and ‘Ire’ takes up two lines instead of one.](https://cdn-images-1.medium.com/max/2000/1*w0WQqsc1DhH17EyNOKPhuQ.png)*Here, the example sentences for ‘Incense’ and ‘Ire’ takes up two lines instead of one.*

According to my code logic, since there is no ‘:’ sign in the second line (nor a ‘=’ sign, for that matter), the contents in the line would not be treated as a part of the example. As a result, this statement would make the last ‘else’ part true and execute the code written in it. Considering all this, I modified the code as below:

![Modification — inserted another ‘elif’ condition and rewrote code for the ‘else’ part](https://cdn-images-1.medium.com/max/2000/1*QWB0BmrLXLpNfSKOCYDkDA.png)*Modification — inserted another ‘elif’ condition and rewrote code for the ‘else’ part*

Here, hasNumbers() is a function which checks whether a given line has numbers in it. I defined it as follows:

![](https://cdn-images-1.medium.com/max/2000/1*UPwTR-3qFOQdWRaKKu9H_w.png)

What this does is that it collects the second line of the example if all other conditions fail, combines it with the first line and then adds it the corresponding list as before.

To my disappointment, this didn’t work and instead showed an error that the index was out of range. I was dumbstruck, as every line of code seemed to be logically correct in my view.

After hours of madness, my brother showed me a way to fetch the line numbers where the error occurred. One of the main skills in programming is the ability the debug the program, to properly check for possible errors and maintain a continuous flow.

Interestingly, the following addition to the code reported that the error occurred at around line number 1750 of the text file.

![The Enumerate Function adds a counter to an iterable enabling easy debugging by checking the line number where the error occurred.](https://cdn-images-1.medium.com/max/2000/1*30ejG-0YThfCRmyYbgunOQ.png)*The Enumerate Function adds a counter to an iterable enabling easy debugging by checking the line number where the error occurred.*

This meant that the program worked well till that line number and that my code was correct! The problems lay in my wrong assumptions and also the text file thanks to its heterogeneity.

This time around, I noticed some keys were not by their numbers which caused problems in the logic flow. I rectified the mistakes by further modifying the code as follows:

![This too worked well for a while but then snap!](https://cdn-images-1.medium.com/max/2000/1*eHtwzbul3Tah8UmR6YuvUg.png)*This too worked well for a while but then snap!*

This worked well till line 4428 of the text file but crashed right after. I checked that line number on the text file itself but that didn’t help much. Then I realized, much to my happiness, that it must be the last line. The whole program worked on the clean list which was void of newlines and spaces. I printed the last line of the clean list and compared it with the last line of the text file. They matched!

I was extremely happy to know this as it meant the program was executed until the end. The only reason why it crashed was that after the last sentence none of the code made sense. My conditionals were designed to every time check the next line also, along with the current line. Since there was no line after the last line, it crashed.

So I wrote an additional line of code to cover that up:

![](https://cdn-images-1.medium.com/max/2000/1*Bv66X-XT_K60WBcifzxd1Q.png)

Everything worked now. Finally! Now all I had to was to assign the keys to corresponding values and that’s that! I took a break at this moment, considering that my project was finally over. I would add some final touches to it later.

But before taking a break, I decided to enclose every code inside various functions so as to make the code look neat. I already had much trouble navigating up and down the lines of code. So I decided to take a break after doing this.

However, after doing so, the program started giving variable scope errors. I realized that this was because variables declared inside functions cannot be called directly from outside the function as they are in the local namespace. Unwilling to make further changes due to that lame error I decided to revert back to the same code with which I had been hitting my head from the start.

However, to my utter disbelief, the program didn’t work in the same way as it did before. In fact, it didn’t work at all! I simply couldn’t figure out the reason (and I still can’t!). I was utterly depressed for the rest of the day. It was like experiencing a nightmare even before falling asleep!

Fortunately and miraculously, the code worked the next day after I made some careful changes. I made sure that I made many beta files (for each change made) thereafter so as to avoid such unnecessary chaos.

After a few more hours, I was able to finally complete my program (but not until I consumed 4 full days). I made few more changes such as:

i) modifying the ‘hasNumbers’ function to ‘hasNumbersDot’ function and excluding the regex I made earlier in the program. This matched the keys more efficiently as it had no assumptions and hence no exceptions. The code for it is as follows:

![This returns ‘True’ if it matches lines containing a number and a word at the beginning of the line instead of the previous one which would match the same anywhere in the line.](https://cdn-images-1.medium.com/max/2000/1*Un9YxNqocYZzRMOwSsEeNA.png)*This returns ‘True’ if it matches lines containing a number and a word at the beginning of the line instead of the previous one which would match the same anywhere in the line.*

ii) replacing the regex condition and the code for obtaining keys from the clean list.

![Replaced this with the below code](https://cdn-images-1.medium.com/max/2000/1*qo3k1ixMwDwFb9obkR4Plg.png)*Replaced this with the below code*

![This is much more efficient than the previous one as it makes use of the already defined ‘hasNumbersDot’ function. Also, it matched the full line (full key)](https://cdn-images-1.medium.com/max/2000/1*T8HPTRUS1CpQHKiHUWGIZQ.png)*This is much more efficient than the previous one as it makes use of the already defined ‘hasNumbersDot’ function. Also, it matched the full line (full key)*

iii) combining the ‘if’ conditions in the ‘examples extraction’ part

![Prior to this modification, the last example sentence could not be extracted from each key](https://cdn-images-1.medium.com/max/2000/1*ldOMziFFJFAcoTODwUjumA.png)*Prior to this modification, the last example sentence could not be extracted from each key*

iv) materializing the code for dictionary key assignment

![](https://cdn-images-1.medium.com/max/2000/1*kumgW4n8n490qKHh8gxDSg.png)

Also, after some trial and error, I was able to convert the data obtained into a beautifully structured CSV file:

![](https://cdn-images-1.medium.com/max/2482/1*014pQ3vfiLelKQQ7ildAWg.png)

![Code for obtaining CSV file](https://cdn-images-1.medium.com/max/2000/1*QAL7Ad3FN757DA39IjnCEA.png)*Code for obtaining CSV file*
> You can check out my github repository on my [profile](https://github.com/pranavmodx) for viewing the full code for the program including the text file and csv file.

Overall, it was a great experience. I got to learn so much out of this project. I also gained more confidence in my skills. Despite some unfortunate events (programming involves such things :P), I was finally able to complete the given task.

One last thing! Recently, I came across a hilarious meme regarding the stages of debugging which is so relatable to my experience that I can’t resist sharing. xD

![](https://cdn-images-1.medium.com/max/2000/1*9fJm-Rv9q-9auAqCMBPCFQ.png)

Thanks for making it all the way until here (even if you skipped most of it to check out the final result :P).
