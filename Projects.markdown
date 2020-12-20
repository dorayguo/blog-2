---
layout: page
title: Projects
permalink: /projects/
---


**Fall 2020**

[Personal Website](#personal-website-2020)

[Web Scraping scripts](#web-scraping-2020)

**Summer 2020**

[Microsoft Explore Intern Project](#explore-project-2020)

[Ciao (MHacks 13)](#ciao-2020)

**Fall 2019**
[ReConnect (MHacks 12)](#reconnect-2019)

## Fall 2020
### Personal Website<a name="personal-website-2020"></a>
This website is a place for my reflections, thoughts, and project descriptions.

|Timeline|Technologies|
|--|--|
| December 2020 | Jekyll, Github Pages, Photoshop |

#### Design Process
I was inspired by various other blogs and decided on a few factors for my website...
 - Simplicity: easy way of reading
 - Content-driven: contains only substance
 - Personality: feelings of adventure, coziness, and pleasantness

Here are my final website layouts:
![website layouts](/assets/website-layout.PNG)

I took a great deal of inspiration from [Tom Preston-Werner's blog](https://tom.preston-werner.com/), which has a clear display of content and minimal noise between page transitions.

For personality, I wanted to let visitors feel like they're taking an adventure, while feeling warm and cozy inside. 

For the background, I enjoyed [these designs](https://www.pinterest.com/pin/456411743490215586/). The paper-like texture and imperfections from the middle design are warm and personal. I really like the soft tan background color; it's as if one were reading a book. The moon and stars from the bottom design give a touch of fantasy and magnificence.

Here is a sample design of the homepage with color:
![homepage design with color](/assets/website-design-1.png)

I chose an elegant and sweet font family. The contrasting and complementing colors allow easy shift of attention. To reduce clutter, I conveyed order through structuring the font sizes.

For the about me page, I carried on similar elements and color palette. I'm still deciding another possible background colors. This one is lighter and makes the website look cleaner.

Here is a sample design of the about me page with color:
![about me page design with color](/assets/website-design-2.png)

#### Development Process
*December 14, 2020:*
The site is currently accessible through [dorayguo.github.io](http://dorayguo.github.io/). Because of build issues, I am currently modifying this site through Github. 

I will be gradually start adding blog posts and project content. Design integration will be delayed for now.

### Web Scraping Scripts<a name="web-scraping-2020"></a>
#### 1. Course Availability Checker

After watching Kalle Hallden's [Youtube video](https://www.youtube.com/watch?v=CHUxmVVH2AQ&t=246s) about basic of web scraping, I thought back to one of my previous ideas. While registering for Fall 2020, it was a lot of repeated work to check if a class had open seats, especially if you are monitoring multiple classes everyday.

Thus came the idea of using web scraping to check for course availability. I tried to implement this before, but I was confused on where to start, as well as what more you have to do to scrape dynamic websites.

Kalle Hallden's video helped guide me through setting up and doing basic navigation with Selenium. Then, I did my own research and exploration.

**Brief walkthrough of code**

After navigating to the [University of Michigan's course catalog](https://www.lsa.umich.edu/cg/default.aspx), I passed in console input into the website's search engine:

    input_form.send_keys(student_input)
    input_form.send_keys(Keys.ENTER)

After landing into [the page for search results](https://www.lsa.umich.edu/cg/cg_results.aspx?termArray=w_21_2320&cgtype=ug&show=20&department=EECS&catalog=370), it clicks on the first class item it sees:

    browser.find_element_by_xpath('//*[@id="contentMain_panelResults"]/div[5]/div/div[1]/div/a').click()

This pulls up [the page that displays all lectures, discussion sections, and labs for the corresponding class](https://www.lsa.umich.edu/cg/cg_detail.aspx?content=2320EECS370001&termArray=w_21_2320). I loop through all of those aforementioned items:

    for class_row in browser.find_elements_by_class_name('clsschedulerow'):
 
For each class item, I save the lecture/section number, the course number, the number of open seats, the length of the waitlist (if there is one), and the day/time/location into a string. I also deal with edge cases in this same loop. 

After some stylizations to the string, I append each class item's details to a list:

    classes_list.append(each_class)

Then I print the list:

    for c in classes_list:
	    print(c)

This is accompanied by a small summary of whether there are any classes available and whether there are no discussion sections/lab available.

Lastly, it provides the option to check for further class details by redirecting to the corresponding class syllabus or Atlas:

    further_input = input("Would you like to redirect to a possible [s]yllabus, [a]tlas profile, or do [n]othing? [s/a/n]?: ")

#### 2. Latest News from *The Atlantic* and *Scientific American*
With momentum from my last web scraping project, I thought about more ideas that I could implement web scraping. One idea was displaying all the latest news articles from *The Atlantic* or *Scientific American*. The reason why is I thought of it is because I find myself paying attention to the news less and less during remote school.

Like the course availability checker, the latest news script uses Python and Selenium. I won't go through the code like before, because most of the syntax is the same.

Some logic is different. For example, when I choose *The Atlantic*, the console displays a list of all of the latest article titles, then prompting me if I would like to read the description of any of the articles. If I proceed with reading one of them, I am prompted if I would like to read the article. After I answer yes and receive a new tab with that article or I answer no, I am prompted if I would like to read an article description until I answer no.

The *Scientific American* website is different, so functionalities are added and deleted correspondingly. However, most of the implementation is the same with choosing *The Atlantic*.

I find that using this script condenses the information, and it becomes easier to read without website noise.


|Timeline|Technologies|
|--|--|
| December 2020 | Python, Selenium, MSEdgeDriver |

## Summer 2020
### Microsoft Explore Intern Project<a name="explore-project-2020"></a>
In a team of 3 interns, we designed and developed a C# API for developers to self-test their 3rd party SaaS applications for Microsoft’s standards before onboarding to the [Azure Active Directory gallery](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-howto-app-gallery-listing)

I worked on created robust test features to check SaaS applications for the correct effects and responses for PUT and DELETE requests and edge cases, as well as integrating the executable application into a local endpoint.

I also organized and conducted 10 cognitive walkthroughs with existing customers to collect feedback on our previous onboarding process and our future design.

|Timeline|Technologies|
|--|--|
| May - Aug 2020 | C#, Git |

#### Quantifiables
 -  Automated process time to check SaaS application for correct configurations from 6 months to *2 weeks*
 - Identified 6 issues in existing onboarded applications with updated testing standards

*Check out [this post]({%  post_url  2020-08-30-my-Summer-2020-internship %}) for what I've learned from this internship.*

### Ciao<a name="ciao-2020"></a>
At MHacks 13, our team of 4 created a skill-sharing platform connected to Firebase and TensorFlow recommendation system. The user can earn currency from mentoring others, learn from mentors by spending currency, and chat.

I developed the homepage, the explore page that dynamically generated cards with mentors from the recommendation system, and the profile page of other users that query their respective mentor data from Firebase.

|Timeline|Technologies|
|--|--|
| Aug 2020 | Python (Flask), Javascript, HTML, CSS, Tensorflow, Firebase |

#### Details:
 - Wolfram Award for Top 30 Hacks.
 - [Figma Designs](https://www.figma.com/file/hBAk5ZdN0d8pmCORq4CrYv/MHACKS?node-id=0%3A1)
 - [Github Repo](https://github.com/yma17/mhacks-13-project)
 - [Ciao | Devpost](https://devpost.com/software/ciao-ejko35)

## Fall 2019
### ReConnect <a name="reconnect-2019"></a>
At MHacks 12, our team of 4 created a site that reminds lonely users of their grateful moments or possible activities to do and asks happy users for things that they are grateful for.

|Timeline|Technologies|
|--|--|
| Sept 2019 | jQuery, Bootstrap, HTML, and CSS |

#### Details:
 - Presented at final demo.
 - [ReConnect | Devpost](https://devpost.com/software/reconnect-dwjnzb)
