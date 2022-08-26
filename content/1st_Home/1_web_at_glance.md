+++
title = "1.1 Web at a glance"
menuTitle = "1.1 Web at a glance"
weight = 2
+++

- [**1. Web at a glance**](#1-web-at-a-glance)
  - [**1.1 Overview of a webpage**](#11-overview-of-a-webpage)
    - [**1.1.1 HTML**](#111-html)
    - [**1.1.2 CSS**](#112-css)
    - [**1.1.3 JavaScript**](#113-javascript)


<span style="font-family:Impact; font-size:1.5em;color:red;">Is web crawling and scraping legal?</span>
><span style="font-family:Georgia;color:rgb(30,144,255);font-size:1.5em">Octoparse</span> <span style="font-family:Georgia; font-size:1em;">: If you’re doing web crawling for your own purposes, then it is legal as it falls under fair use doctrine. The complications start if you want to use scraped data for others, especially commercial purposes. As long as you are not crawling at a disruptive rate and the source is public you should be fine.</span> <br> 
> <span style="font-family:Georgia;color:rgb(139,0,0);font-size:1.5em">Quora</span> <span style="font-family:Georgia; font-size:1em;">: You can crawl any page you like, scraping in itself is not illegal. The worst case scenario would be if you got blocked by the website if you do not follow the rules stated in the robots.txt.</span>

|Web crawling| Vs. |Web scraping|
|:---|:---:|:---|
|- Web crawling, also known as Indexing is used to index the information on the page using bots also known as crawlers.<br> - Web Crawlers are basically used by major search engines like Google, Bing, Yahoo, statistical agencies, and large online aggregators.<br>- When a bot crawls a website, it goes through every page and every link, until the last line of the website, looking for ANY information.<br> - **The web crawling process usually captures generic information.**|🆚|- Web scraping, also known as web data extraction, is similar to web crawling in that it identifies and locates the target data from web pages.<br> - **The key difference, is that with web scraping, we know the exact data set identifier** e.g. an HTML element structure for web pages that are being fixed, from which data needs to be extracted.<br> - Web scraping is an automated way of extracting specific data sets using bots which are also known as ‘scrapers’.|

**What is a robots.txt file?** Robots.txt is a text file webmasters create to instruct web robots (typically search engine robots) how to crawl pages on their website. The robots.txt file is part of the the robots exclusion protocol (REP), a group of web standards that regulate how robots crawl the web, access and index content, and serve that content up to users.

## **1. Web at a glance** 
***What is the Web?*** 

The **World Wide Web** (**WWW**), commonly known as the **Web**, is an information system. It is an amazing collection of interconnected documents. 

**Webpage**/**Website** is a metaphor applied to the web.

The purpose of a **Web browser** (Chrome, Edge, Firefox, Safari) is to read HTML documents and display them correctly. A browser does not display the HTML tags, but uses them to determine how to display the document

### **1.1 Overview of a webpage**
A webpage generally consists of three parts, namely HTML(超文本标记语言), CSS(层叠样式表) and JavaScript(活动脚本语言).

- **HTML** provides the basic structure of sites, which is enhanced and modified by other technologies like CSS and JavaScript.
- **CSS** is used to control presentation, formatting, and layout.
- **JavaScript** is used to control the behavior of different elements.
  
*如果用人体来比喻，HTML 是人的骨架，并且定义了人的嘴巴、眼睛、耳朵等要长在哪里。CSS 是人的外观细节，如嘴巴长什么样子，眼睛是双眼皮还是单眼皮，是大眼睛还是小眼睛，皮肤是黑色的还是白色的等。JavaScript 表示人的技能，例如跳舞、唱歌或者演奏乐器等。*

#### **1.1.1 HTML**
HTML stands for HyperText Markup Language. "Markup language" means that, rather than using a programming language to perform functions, HTML uses **tags** to identify different types of content and the purposes they each serve to the webpage.

Let's start with a simple webpage without CSS and JavaScript：[webpage_raw](https://htmlpreview.github.io/?https://github.com/RC-Web-crawler/Hugo-site/blob/main/content/1_web_at_glance/webpage_raw.html)

HTML Document:
```
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>爬虫小组的测试页</title>
</head>

<body>

    <h1>欢迎来到爬虫小组的网页！</h1>
    <p>这是一个简单的测试页</p>

    <h2>团队成员与重要日期</h2>
    <p><b>2020年6月10日</b> — 于昊永加入诺华的日子</p>
    <p><b>2020年8月20日</b> — 杨帆加入诺华的日子</p>
    <p><b>2021年6月1日</b> — 王崧人加入诺华的日子</p>
    <p><b>2021年7月1日</b> — 韩梦岳加入诺华的日子</p>
    <p><b>2021年7月1日</b> — 滕书言加入诺华的日子</p>
    <p><b>2021年7月1日</b> — 姚艾文加入诺华的日子</p>

    <h2><img id="myImage" src="https://www.w3schools.com/js/pic_bulboff.gif" style="width:30px">更多信息 </h2>
    <p>Gitlab: 
        <a href="http://gitlabce.apps.dit-prdocp.novartis.net/YUHAY/web-crawler-do.git">Web Crawler DO</a>
    </p>
    
</body>
</html>
```
You can see a lot of tags in this document, such as `<html>`, `</html>`, `<head>`, `<body>`, `<img>`, etc.

#### **1.1.2 CSS**
CSS stands for Cascading Style Sheets. This programming language dictates how the HTML elements of a website should actually appear on the frontend of the page.

Let's see the new webpage after adding a CSS style: [webpage_css](https://htmlpreview.github.io/?https://github.com/RC-Web-crawler/Hugo-site/blob/main/content/1_web_at_glance/webpage_css.html)

```
    <style type="text/css">
    @import url('https://fonts.googleapis.com/css2?family=ZCOOL+KuaiLe&display=swap');
    body {background-image: url('https://www.statnews.com/wp-content/uploads/2018/05/Novartis-1.jpg');
        font-family: 'ZCOOL KuaiLe';}
    h1 {color: blanchedalmond;font-size: 50px;}
    p {color:tomato; font-size: 25px;}
    h2 {color: yellow;font-size: 30px;}
    a {color:turquoise;}
    </style>
```
#### **1.1.3 JavaScript**
JavaScript is a logic-based programming language that can be used to modify website content and make it behave in different ways in response to a user's actions. Most of the dynamic behavior you'll see on a web page is thanks to JavaScript, which augments a browser's default controls and behaviors.

Let's see the new webpage after applying a JavaScript：[webpage_js](https://htmlpreview.github.io/?https://github.com/RC-Web-crawler/Hugo-site/blob/main/content/1_web_at_glance/webpage_js.html)

