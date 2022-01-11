+++
title = "CSS selectorts & Xpath"
menuTitle = "3. CSS selectorts & Xpath"
weight = 3
+++

========

#### songren

#### 12/27/2021

Introduction
============

XPath is a query language for selecting nodes from an XML document. In addition, XPath may be used to compute values from the content of an XML document. XPath was defined by the World Wide Web Consortium. CSS selectors are used to select the content you want to style. Selectors are the part of CSS rule set. CSS selectors select HTML elements according to its id, class, type, attribute etc.(CSS selector: [https://www.w3school.com.cn/cssref/css\_selectors.asp](https://www.w3school.com.cn/cssref/css_selectors.asp), Xpath: [https://www.w3school.com.cn/xpath/index.asp](https://www.w3school.com.cn/xpath/index.asp))

Summary
=======

CSS selector Summary
--------------------

### Syntax

Syntax

Example

Result

.class

.intro

Selects all elements with class=“intro”

.class1.class2

.name1.name2

Selects all elements with both name1 and name2 set within its class attribute

.class1 .class2

.name1 .name2

Selects all elements with name2 that is a descendant of an element with name1

#id

#firstname

Selects the element with id=“firstname”

asterisk

asterisk

Selects all elements

element

p

Selects all <p> elements

element.class

p.intro

Selects all <p> elements with class=“intro”

element,element

div, p

Selects all <div> elements and all <p> elements

element element

div p

Selects all <p> elements inside <div> elements

element>element

div > p

Selects all <p> elements where the parent is a <div> element

element+element

div + p

Selects the first <p> element that is placed immediately after <div> elements

element1~element2

p ~ ul

Selects every <ul> element that is preceded by a <p> element

\[attribute\]

\[target\]

Selects all elements with a target attribute

\[attribute=value\]

\[target=\_blank\]

Selects all elements with target="\_blank"

\[attribute~=value\]

\[title~=flower\]

Selects all elements with a title attribute containing the word “flower”

\[attribute|=value\]

\[lang|=en\]

Selects all elements with a lang attribute value equal to “en” or starting with “en-”

\[attribute^=value\]

a\[href^=“https”\]

Selects every <a> element whose href attribute value begins with “https”

\[attribute$=value\]

a\[href$=“.pdf”\]

Selects every <a> element whose href attribute value ends with “.pdf”

\[attribute\*=value\]

a\[href\*=“w3schools”\]

Selects every <a> element whose href attribute value contains the substring “w3schools”

### Expression

Expression

Example

Result

:active

a:active

Selects the active link

::after

p::after

Insert something after the content of each <p> element

::before

p::before

Insert something before the content of each <p> element

:checked

input:checked

Selects every checked <input> element

:default

input:default

Selects the default <input> element

:disabled

input:disabled

Selects every disabled <input> element

:empty

p:empty

Selects every <p> element that has no children (including text nodes)

:enabled

input:enabled

Selects every enabled <input> element

:first-child

p:first-child

Selects every <p> element that is the first child of its parent

::first-letter

p::first-letter

Selects the first letter of every <p> element

::first-line

p::first-line

Selects the first line of every <p> element

:first-of-type

p:first-of-type

Selects every <p> element that is the first <p> element of its parent

:focus

input:focus

Selects the input element which has focus

:fullscreen

:fullscreen

Selects the element that is in full-screen mode

:hover

a:hover

Selects links on mouse over

:in-range

input:in-range

Selects input elements with a value within a specified range

:indeterminate

input:indeterminate

Selects input elements that are in an indeterminate state

:invalid

input:invalid

Selects all input elements with an invalid value

:lang(language)

p:lang(it)

Selects every <p> element with a lang attribute equal to “it” (Italian)

:last-child

p:last-child

Selects every <p> element that is the last child of its parent

:last-of-type

p:last-of-type

Selects every <p> element that is the last <p> element of its parent

:link

a:link

Selects all unvisited links

::marker

::marker

Selects the markers of list items

:not(selector)

:not(p)

Selects every element that is not a <p> element

:nth-child(n)

p:nth-child(2)

Selects every <p> element that is the second child of its parent

:nth-last-child(n)

p:nth-last-child(2)

Selects every <p> element that is the second child of its parent, counting from the last child

:nth-last-of-type(n)

p:nth-last-of-type(2)

Selects every <p> element that is the second <p> element of its parent, counting from the last child

:nth-of-type(n)

p:nth-of-type(2)

Selects every <p> element that is the second <p> element of its parent

:only-of-type

p:only-of-type

Selects every <p> element that is the only <p> element of its parent

:only-child

p:only-child

Selects every <p> element that is the only child of its parent

:optional

input:optional

Selects input elements with no “required” attribute

:out-of-range

input:out-of-range

Selects input elements with a value outside a specified range

::placeholder

input::placeholder

Selects input elements with the “placeholder” attribute specified

:read-only

input:read-only

Selects input elements with the “readonly” attribute specified

:read-write

input:read-write

Selects input elements with the “readonly” attribute NOT specified

:required

input:required

Selects input elements with the “required” attribute specified

:root

:root

Selects the document’s root element

::selection

::selection

Selects the portion of an element that is selected by a user

:target

#[news:target](news:target)

Selects the current active #news element (clicked on a URL containing that anchor name)

:valid

input:valid

Selects all input elements with a valid value

:visited

a:visited

Selects all visited links

XPATH Summary
-------------

### Syntax

Expression

Description

Example

Result

nodename

Selects all nodes with the name “nodename”

bookstore

Selects all nodes with the name “bookstore”

/

Selects from the root node

/bookstore

Selects the root element bookstore

//

Selects nodes in the document from the current node that match the selection no matter where they are

bookstore/book

Selects all book elements that are children of bookstore

.

Selects the current node

//book

Selects all book elements no matter where they are in the document

..

Selects the parent of the current node

bookstore//book

Selects all book elements that are descendant of the bookstore element, no matter where they are under the bookstore element

@

Selects attributes

//@lang

Selects all attributes that are named lang

\*

Matches any element node

/bookstore/\*

Selects all the child element nodes of the bookstore element

@\*

Matches any attribute node

//\*

Selects all elements in the document

node()

Matches any node of any kind

//title\[@\*\]

Selects all title elements which have at least one attribute of any kind

Note: If the path starts with a slash ( / ) it always represents an absolute path to an element!

### Axes

Axesname

Description

Example

Result

ancestor

Selects all ancestors (parent, grandparent, etc.) of the current node

ancestor::book

Selects all book nodes that are ancestor of the current node

ancestor-or-self

Selects all ancestors (parent, grandparent, etc.) of the current node and the current node itself

attribute

Selects all attributes of the current node

attribute::\*

Selects all attributes of the current node

child

Selects all children of the current node

child::\*/child::price

Selects all price grandchildren of the current node

descendant

Selects all descendants (children, grandchildren, etc.) of the current node

descendant::book

Selects all book descendants of the current node

descendant-or-self

Selects all descendants (children, grandchildren, etc.) of the current node and the current node itself

following

Selects everything in the document after the closing tag of the current node

following::text()

Selects all text node that are everything after the current node

following-sibling

Selects all siblings after the current node

following-sibling::node()

Selects all siblings after the current node

namespace

Selects all namespace nodes of the current node

parent

Selects the parent of the current node

parent::book

Selects all book nodes that are parent of the current node

preceding

Selects all nodes that appear before the current node in the document, except ancestors, attribute nodes and namespace nodes

preceding::price

Selects all price nodes that appear before the current node

preceding-sibling

Selects all siblings before the current node

preceding-sibling::book\[price>50.0\]

Selects book nodes with price>50 from siblings before the current node

self

Selects the current node

self::\*

Selects all in the current node

### Operator

Operator

Description

Example

|

Computes two node-sets

//book | //cd

+

Addition

6 + 4

\-

Subtraction

6 - 4

\*

Multiplication

6 \* 4

div

Division

8 div 4

\=

Equal

price=9.80

!=

Not equal

price!=9.80

<

Less than

price<9.80

<=

Less than or equal to

price<=9.80

\>

Greater than

price>9.80

\>=

Greater than or equal to

price>=9.80

or

or

price=9.80 or price=9.70

and

and

price>9.00 and price<9.90

mod

Modulus (division remainder)

5 mod 2

Examples
========

HTML Structure
--------------

    ## <!DOCTYPE html>
    ## <html>
    ## <head>
    ## <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    ## <meta charset="utf-8">
    ## <title>Webscrap introduction</title>
    ## </head>
    ## <body>
    ## <div class="class1" id="div1">
    ##       <p class="class3">
    ##         Welcome 2022!
    ##          <t class="text">
    ##          Beat COVID-19!
    ##          </t></p>
    ##  </div>
    ##  <div class="class2" id="div2">
    ##       <p class="class3" href="https://en.wikipedia.org/wiki/Cat">
    ##         Happy Spring Festival!
    ##          <t class="text"> Dumpling YYDS! </t><price>0.00</price></p>
    ##  </div>
    ##  <div class="class1 class2" id="div3">
    ##       <p class="class3" href="https://en.wikipedia.org/wiki/Cat">
    ##         Happy Valentine's Day!
    ##          <t class="text"> Let's romantic! </t><price>100.0</price></p>
    ##       <p class="class4" href="https://en.wikipedia.org/wiki/Cat">
    ##         Happy Lantern Festival!
    ##          <t class="text"> Sweet Dumpling YYDS! </t><price>0.0</price></p>
    ##  </div>
    ## </body>
    ## </html>
    ## 

Example 1
---------

### css selector

    check_element_text(html = html, css = "head > title")

    ## [1] "Webscrap introduction"

### xpath

    check_element_text(html = html, xpath = "/html/head/title")

    ## [1] "Webscrap introduction"

Example 2
---------

### css selector

    check_element_text(html = html, css = "body p")

    ## [1] "   Welcome 2022!        Beat COVID-19!    "             
    ## [2] "   Happy Spring Festival!     Dumpling YYDS! 0.00"      
    ## [3] "   Happy Valentine's Day!     Let's romantic! 100.0"    
    ## [4] "   Happy Lantern Festival!     Sweet Dumpling YYDS! 0.0"

### xpath

    check_element_text(html = html, xpath = "//body//p")

    ## [1] "   Welcome 2022!        Beat COVID-19!    "             
    ## [2] "   Happy Spring Festival!     Dumpling YYDS! 0.00"      
    ## [3] "   Happy Valentine's Day!     Let's romantic! 100.0"    
    ## [4] "   Happy Lantern Festival!     Sweet Dumpling YYDS! 0.0"

Example 3
---------

### css selector

    check_element_text(html = html, css = "t")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       " Let's romantic! "     
    ## [4] " Sweet Dumpling YYDS! "

### xpath

    check_element_text(html = html, xpath = "//t")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       " Let's romantic! "     
    ## [4] " Sweet Dumpling YYDS! "

Example 4
---------

### css selector

    check_element_text(html = html, css = "div:first-of-type")

    ## [1] "    Welcome 2022!        Beat COVID-19!     "

    check_element_text(html = html, css = "div:nth-of-type(2)")

    ## [1] "    Happy Spring Festival!     Dumpling YYDS! 0.00 "

    check_element_text(html = html, css = "div:last-of-type")

    ## [1] "    Happy Valentine's Day!     Let's romantic! 100.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 0.0 "

### xpath

    check_element_text(html = html, xpath = "//div[position()=1]")

    ## [1] "    Welcome 2022!        Beat COVID-19!     "

    check_element_text(html = html, xpath = "//div[2]")

    ## [1] "    Happy Spring Festival!     Dumpling YYDS! 0.00 "

    check_element_text(html = html, xpath = "//div[last()]")

    ## [1] "    Happy Valentine's Day!     Let's romantic! 100.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 0.0 "

Example 5
---------

### css selector

    check_element_text(html = html, css = "div#div2")

    ## [1] "    Happy Spring Festival!     Dumpling YYDS! 0.00 "

### xpath

    check_element_text(html = html, xpath = "//div[@id='div2']")

    ## [1] "    Happy Spring Festival!     Dumpling YYDS! 0.00 "

Example 6
---------

### css selector

    check_element_text(html = html, css = "t.text")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       " Let's romantic! "     
    ## [4] " Sweet Dumpling YYDS! "

### xpath

    check_element_text(html = html, xpath = "//t[@class='text']")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       " Let's romantic! "     
    ## [4] " Sweet Dumpling YYDS! "

Example 7
---------

### css selector

    check_element_text(html = html, css = "*.class3")

    ## [1] "   Welcome 2022!        Beat COVID-19!    "         
    ## [2] "   Happy Spring Festival!     Dumpling YYDS! 0.00"  
    ## [3] "   Happy Valentine's Day!     Let's romantic! 100.0"

### xpath

    check_element_text(html = html, xpath = "//*[@class='class3']")

    ## [1] "   Welcome 2022!        Beat COVID-19!    "         
    ## [2] "   Happy Spring Festival!     Dumpling YYDS! 0.00"  
    ## [3] "   Happy Valentine's Day!     Let's romantic! 100.0"

Example 8
---------

### css selector

    check_element_text(html = html, css = "t, price")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       "0.00"                  
    ## [4] " Let's romantic! "      "100.0"                  " Sweet Dumpling YYDS! "
    ## [7] "0.0"

### xpath

    check_element_text(html = html, xpath = "//t | //price")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       "0.00"                  
    ## [4] " Let's romantic! "      "100.0"                  " Sweet Dumpling YYDS! "
    ## [7] "0.0"

Example 9
---------

### css selector

    check_element_text(html = html, css = "div t")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       " Let's romantic! "     
    ## [4] " Sweet Dumpling YYDS! "

### xpath

    check_element_text(html = html, xpath = "//div/descendant::t")

    ## [1] "    Beat COVID-19!    " " Dumpling YYDS! "       " Let's romantic! "     
    ## [4] " Sweet Dumpling YYDS! "

    check_element_text(html = html, xpath = "//t/ancestor::div")

    ## [1] "    Welcome 2022!        Beat COVID-19!     "                                                                 
    ## [2] "    Happy Spring Festival!     Dumpling YYDS! 0.00 "                                                          
    ## [3] "    Happy Valentine's Day!     Let's romantic! 100.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 0.0 "

Example 10
----------

### css selector

    ## Not avaiable

### xpath

    check_element_text(html = html, xpath = "//p[price>50.0]/t")

    ## [1] " Let's romantic! "

// add bootstrap table styles to pandoc tables function bootstrapStylePandocTables() { $('tr.odd').parent('tbody').parent('table').addClass('table table-condensed'); } $(document).ready(function () { bootstrapStylePandocTables(); }); $(document).ready(function () { window.buildTabsets("TOC"); }); $(document).ready(function () { $('.tabset-dropdown > .nav-tabs > li').click(function () { $(this).parent().toggleClass('nav-tabs-open'); }); }); $(document).ready(function () { // temporarily add toc-ignore selector to headers for the consistency with Pandoc $('.unlisted.unnumbered').addClass('toc-ignore') // move toc-ignore selectors from section div to header $('div.section.toc-ignore') .removeClass('toc-ignore') .children('h1,h2,h3,h4,h5').addClass('toc-ignore'); // establish options var options = { selectors: "h1,h2,h3", theme: "bootstrap3", context: '.toc-content', hashGenerator: function (text) { return text.replace(/\[.\\\\/?&!#<>\]/g, '').replace(/\\s/g, '\_'); }, ignoreSelector: ".toc-ignore", scrollTo: 0 }; options.showAndHide = true; options.smoothScroll = true; // tocify var toc = $("#TOC").tocify(options).data("toc-tocify"); }); (function () { var script = document.createElement("script"); script.type = "text/javascript"; script.src = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML\_HTMLorMML"; document.getElementsByTagName("head")\[0\].appendChild(script); })();