---
layout: post
title:      "CLI Data Gem Portfolio Project"
date:       2019-06-27 11:42:12 -0400
permalink:  bridging_the_gap_healthcare_and_technology
---

Being primarily involved in the healthcare field, when I heard that we had to make a program that took a page which had a list of information and use it to build a CLI gem, I naturally turned to using a medication website. However, after playing around with this particular kind of website and talking with Lantz after trying to scrape it, it was clear that it was going ot be much harder than I was ready to handle.
I have many friends who are in law enforcement, so I resorted to using a website that listed several police stations.

**THE SET-UP:**

Setting up the whole project was slightly scary. However, after reviewing several videos that were provided to us, and doing a walkthrough with Lantz it became a bit more clear and straightforward. 
Setting up the structure/"bones" of my classes and methods was also pretty straight forward once I realized that everything would start to "fall into place" after I stopped thinking "I can't do this" (of course only until I circle back to that feeling after encountering yet another error).
Scraping was one of the most daunting and nerve-wracking processes that I have ever encountered in an assignment.

**SCRAPING:**

For this website, I decided to scrape the list of police station names as my first level scrape. Then, I scraped the details of the police stations as my second level scrape. 
```
station_list = doc.css(".Table-body .Table-link").map(&:text)
link_list = doc.css(".Table-row").map{|link| link["href"]}
```
Creating this snippet of code was probably the most tedious part of the scraping. Mainly because scraping was a concept that I did not grasp at all the first couple of times that I reviewed it. I had to spend hours reviewing it and watching videos in order to even get the gist of it. 
I also ran into a more challenging issue with the link_list scrape.
My previous code looks like this:
```
link_list = doc.css("a[class=Table-row]").map{|link| link["href"]}
```
However, this was not returning all 25 of the links after running it in irb in my terminal. After debugging and talking things out with a wonderful classmate, we came to the conclusion that I needed to remove the 'a[class=' and replace it with a '.' . This solved this problem and was a huge step forward for me!

**THOUGHTS:**

I am not much of a writer, so writing these blogs are a bit challenging to me. However, there are a few take-aways that I would like to share from doing this project.
1. I will encounter a rollercoaster of emotions when building portfolio projects from scratch (such as going from "I can do it", to "there is no way, I quit", to "my computer is about to go out the window").
2. There is no such thing as a "stupid question" (not asking for help will do more harm than good).
3. There are many ways to do the same thing (try not to get flustered when you see something different).
4. We are all in this together! You are NEVER alone.

