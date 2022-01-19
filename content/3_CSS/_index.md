+++
title = "CSS selectorts & Xpath"
menuTitle = "3. CSS selectorts & Xpath"
weight = 3
+++

## 3.1 Introduction
CSS, Cascading Style Sheets, is a style sheet language used for describing the presentation of a document written in a markup language such as HTML. And CSS selectors are used to select the content you want to style. Selectors are the part of CSS rule set. CSS selectors select HTML elements according to its id, class, type, attribute etc. 

XPath, XML Path Language, is a query language for selecting nodes from an XML document. In addition, XPath may be used to compute values from the content of an XML document. XPath was defined by the World Wide Web Consortium.
[CSS Selector vs XPATH](https://www.w3schools.com/default.asp)

The HyperText Markup Language, or HTML is the standard markup language for documents designed to be displayed in a web browser. It can be assisted by technologies such as Cascading Style Sheets (CSS) and scripting languages such as JavaScript. HTML elements are the building blocks of HTML pages. With HTML constructs, images and other objects such as interactive forms may be embedded into the rendered page. HTML provides a means to create structured documents by denoting structural semantics for text such as headings, paragraphs, lists, links, quotes and other items. HTML elements are delineated by tags, written using angle brackets. Tags such as `<img />` and `<input />` directly introduce content into the page. Other tags such as `<p>` surround and provide information about document text and may include other tags as sub-elements. Browsers do not display the HTML tags, but use them to interpret the content of the page. HTML can embed programs written in a scripting language such as JavaScript, which affects the behavior and content of web pages. Inclusion of CSS defines the look and layout of content. The World Wide Web Consortium (W3C), former maintainer of the HTML and current maintainer of the CSS standards, has encouraged the use of CSS over explicit presentational HTML since 1997. A form of HTML, known as HTML5, is used to display video and audio, primarily using the `<canvas>` element, in collaboration with javascript.

Extensible Markup Language (XML) is a markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable. The design goals of XML emphasize simplicity, generality, and usability across the Internet. It is a textual data format with strong support via Unicode for different human languages. Although the design of XML focuses on documents, the language is widely used for the representation of arbitrary data structures such as those used in web services.
[HTML vs XML](https://www.upgrad.com/blog/html-vs-xml/#:~:text=HTML%20and%20XML%20are%20related,language%20that%20defines%20other%20languages.)


## 3.2 Summary

### 3.2.1 CSS Selector Summary
-----------------------
{{< tabs >}}
{{% tab name="Syntax" %}}

|Selector            |Example              |Result                                                                                          |
|--------------------|---------------------|------------------------------------------------------------------------------------------------|
|.class              |.intro               |Selects all elements with class="intro"                                                         |
|.class1.class2      |.name1.name2         |Selects all elements with both name1 and name2 set within its class attribute                   |
|.class1 .class2     |.name1 .name2        |Selects all elements with name2 that is a descendant of an element with name1                   |
|#id                 |#firstname           |Selects the element with id="firstname"                                                         |
|*                   |*                    |Selects all elements                                                                            |
|element             |p                    |Selects all p elements                                                                          |
|element.class       |p.intro              |Selects all p elements with class="intro"                                                       |
|element,element     |div, p               |Selects all div elements and all p elements                                                     |
|element element     |div p                |Selects all p elements inside div elements                                                      |
|element>element     |div > p              |Selects all p elements where the parent is a div element                                        |
|element+element     |div + p              |Selects the first p element that is placed immediately after div elements                       |
|element1~element2   |p ~ ul               |Selects every ul element that is preceded by a p element                                        |
|[attribute]         |[target]             |Selects all elements with a target attribute                                                    |
|[attribute=value]   |[target=_blank]      |Selects all elements with target="_blank"                                                       |
|[attribute~=value]  |[title~=flower]      |Selects all elements with a title attribute containing the word "flower"                        |
|[attribute&#124;=value]  |[lang&#124;=en] |Selects all elements with a lang attribute value equal to "en" or starting with "en-"           |
|[attribute^=value]  |a[href^="https"]     |Selects every a element whose href attribute value begins with "https"                          |
|[attribute$=value]  |a[href$=".pdf"]      |Selects every a element whose href attribute value ends with ".pdf"                             |
|[attribute*=value]  |a[href*="w3schools"] |Selects every a element whose href attribute value contains the substring "w3schools"           |

{{% /tabs %}}
{{% tab name="Expression" %}}

|Selector            |Example              |Result                                                                                          |
|--------------------|---------------------|------------------------------------------------------------------------------------------------|
|:active             |a:active             |Selects the active link                                                                         |
|::after             |p::after             |Insert something after the content of each p element                                            |
|::before            |p::before            |Insert something before the content of each p element                                           |
|:checked            |input:checked        |Selects every checked input element                                                             |
|:default            |input:default        |Selects the default input element                                                               |
|:disabled           |input:disabled       |Selects every disabled input element                                                            |
|:empty              |p:empty              |Selects every p element that has no children (including text nodes)                             |
|:enabled            |input:enabled        |Selects every enabled input element                                                             |
|:first-child        |p:first-child        |Selects every p element that is the first child of its parent                                   |
|::first-letter      |p::first-letter      |Selects the first letter of every p element                                                     |
|::first-line        |p::first-line        |Selects the first line of every p element                                                       |
|:first-of-type      |p:first-of-type      |Selects every p element that is the first p element of its parent                               |
|:focus              |input:focus          |Selects the input element which has focus                                                       |
|:fullscreen         |:fullscreen          |Selects the element that is in full-screen mode                                                 |
|:hover              |a:hover              |Selects links on mouse over                                                                     |
|:in-range           |input:in-range       |Selects input elements with a value within a specified range                                    |
|:indeterminate      |input:indeterminate  |Selects input elements that are in an indeterminate state                                       |
|:invalid            |input:invalid        |Selects all input elements with an invalid value                                                |
|:lang(language)     |p:lang(it)           |Selects every p element with a lang attribute equal to "it" (Italian)                           |
|:last-child         |p:last-child         |Selects every p element that is the last child of its parent                                    |
|:last-of-type       |p:last-of-type       |Selects every p element that is the last p element of its parent                                |
|:link               |a:link               |Selects all unvisited links                                                                     |
|::marker            |::marker             |Selects the markers of list items                                                               |
|:not(selector)      |:not(p)              |Selects every element that is not a p element                                                   |
|:nth-child(n)       |p:nth-child(2)       |Selects every p element that is the second child of its parent                                  |
|:nth-last-child(n)  |p:nth-last-child(2)  |Selects every p element that is the second child of its parent, counting from the last child    |
|:nth-last-of-type(n)|p:nth-last-of-type(2)|Selects every p element that is the second p element of its parent, counting from the last child|
|:nth-of-type(n)     |p:nth-of-type(2)     |Selects every p element that is the second p element of its parent                              |
|:only-of-type       |p:only-of-type       |Selects every p element that is the only p element of its parent                                |
|:only-child         |p:only-child         |Selects every p element that is the only child of its parent                                    |
|:optional           |input:optional       |Selects input elements with no "required" attribute                                             |
|:out-of-range       |input:out-of-range   |Selects input elements with a value outside a specified range                                   |
|::placeholder       |input::placeholder   |Selects input elements with the "placeholder" attribute specified                               |
|:read-only          |input:read-only      |Selects input elements with the "readonly" attribute specified                                  |
|:read-write         |input:read-write     |Selects input elements with the "readonly" attribute NOT specified                              |
|:required           |input:required       |Selects input elements with the "required" attribute specified                                  |
|:root               |:root                |Selects the document's root element                                                             |
|::selection         |::selection          |Selects the portion of an element that is selected by a user                                    |
|:target             |#news:target         |Selects the current active #news element (clicked on a URL containing that anchor name)         |
|:valid              |input:valid          |Selects all input elements with a valid value                                                   |
|:visited            |a:visited            |Selects all visited links                                                                       |

{{% /tabs %}}
{{< /tabs >}}
[CSS Selector Cheat Sheet](https://frontend30.com/css-selectors-cheatsheet/)

## 3.2.2 XPATH Summary
-----------------------

{{< tabs >}}
{{% tab name="Syntax" %}}

|Expression          |Description                                                                  |Example                                 |Result                                                                          |
|--------------------|-----------------------------------------------------------------------------|----------------------------------------|--------------------------------------------------------------------------------|
|nodename            |Selects all nodes with the name "nodename"                                   |bookstore                               |Selects all nodes with the name "bookstore"                                     |
|/                   |Selects from the root node                                                   |/bookstore                              |Selects the root element bookstore                                              |
|//                  |Selects nodes in the document from the current node that match the selection |bookstore/book                          |Selects all book elements that are children of bookstore                        |
|.                   |Selects the current node                                                     |//book                                  |Selects all book elements no matter where they are in the document              |
|..                  |Selects the parent of the current node                                       |bookstore//book                         |Selects all book elements that are descendant of the bookstore element          |
|@                   |Selects attributes                                                           |//@lang                                 |Selects all attributes that are named lang                                      |
|*                   |Matches any element node                                                     |/bookstore/*                            |Selects all the child element nodes of the bookstore element                    |
|@*                  |Matches any attribute node                                                   |//*                                     |Selects all elements in the document                                            |
|node()              |Matches any node of any kind                                                 |//title[@*]                             |Selects all title elements which have at least one attribute of any kind        |

Note: If the path starts with a slash ( / ) it always represents an absolute path to an element!

{{% /tabs %}}
{{% tab name="Axes" %}}

|Axesname            |Description                                                                                                |Example                                |Result                                                                                                                      |
|--------------------|---------------------------------------------------------------------------------------------------------- |---------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
|ancestor            |Selects all ancestors (parent, grandparent, etc.) of the current node                                      |ancestor::book                         |Selects all book nodes that are ancestor of the current node                                                                |
|ancestor-or-self    |Selects all ancestors (parent, grandparent, etc.) of the current node and the current node itself          |                                       |                                                                                                                            |
|attribute           |Selects all attributes of the current node                                                                 |attribute::*                           |Selects all attributes of the current node                                                                                  |
|child               |Selects all children of the current node                                                                   |child::*/child::price                  |Selects all price grandchildren of the current node                                                                         |
|descendant          |Selects all descendants (children, grandchildren, etc.) of the current node                                |descendant::book                       |Selects all book descendants of the current node                                                                            |
|descendant-or-self  |Selects all descendants (children, grandchildren, etc.) of the current node and the current node itself    |                                       |                                                                                                                            |
|following           |Selects everything in the document after the closing tag of the current node                               |following::text()                      |Selects all text node that are everything after the current node                                                            |
|following-sibling   |Selects all siblings after the current node                                                                |following-sibling::node()              |Selects all siblings after the current node                                                                                 |
|namespace           |Selects all namespace nodes of the current node                                                            |                                       |                                                                                                                            |
|parent              |Selects the parent of the current node                                                                     |parent::book                           |Selects all book nodes that are parent of the current node                                                                  |
|preceding           |Selects all nodes that are before the current node, except ancestors, attribute nodes and namespace nodes  |preceding::price                       |Selects all price nodes that appear before the current node                                                                 |
|preceding-sibling   |Selects all siblings before the current node                                                               |preceding-sibling::book[price>50.0]    |Selects book nodes with price>50 from siblings before the current node                                                      |
|self                |Selects the current node                                                                                   |self::*                                |Selects all in the current node                                                                                             |

{{% /tabs %}}
{{% tab name="Operator" %}}

|Operator            |Description                   |Example                                                                                         |
|--------------------|------------------------------|------------------------------------------------------------------------------------------------|
|&#124;              |Computes two node-sets        |//book &#124; //cd                                                                              |
|+                   |Addition                      |6 + 4                                                                                           |
|-                   |Subtraction                   |6 - 4                                                                                           |
|*                   |Multiplication                |6 * 4                                                                                           |
|div                 |Division                      |8 div 4                                                                                         |
|=                   |Equal                         |price=9.80                                                                                      |
|!=                  |Not equal                     |price!=9.80                                                                                     |
|<                   |Less than                     |price<9.80                                                                                      |
|<=                  |Less than or equal to         |price<=9.80                                                                                     |
|>                   |Greater than                  |price>9.80                                                                                      |
|>=                  |Greater than or equal to      |price>=9.80                                                                                     |
|or                  |or                            |price=9.80 or price=9.70                                                                        |
|and                 |and                           |price>9.00 and price<9.90                                                                       |
|mod                 |Modulus (division remainder)  |5 mod 2                                                                                         |

{{% /tabs %}}
{{< /tabs >}}
[XPATH Cheat Sheet](https://devhints.io/xpath)

## 3.3 Examples
[sample](https://htmlpreview.github.io/?https://github.com/RC-Web-crawler/Hugo-site/blob/main/content/3_ccs/sample.html)

### Example 1:Abusolte path
-----------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R
check_element_text(html = html, css = "body > div > p > t")
```
[1] "Beat COVID-19!"       "Dumpling YYDS!"       "Let's romantic!"     "Sweet Dumpling YYDS!"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R 
check_element_text(html = html, xpath = "/html/body/div/p/t")
```
[1] "Beat COVID-19!"       "Dumpling YYDS!"       "Let's romantic!"     "Sweet Dumpling YYDS!"

{{% /tabs %}}
{{< /tabs >}}

### Example 2:Relative path
-----------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R 
check_element_text(html = html, css = "body t")
```
[1] "Beat COVID-19!"       "Dumpling YYDS!"       "Let's romantic!"     "Sweet Dumpling YYDS!"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R 
check_element_text(html = html, xpath = "//body//t")
```
[1] "Beat COVID-19!"       "Dumpling YYDS!"       "Let's romantic!"     "Sweet Dumpling YYDS!"

{{% /tabs %}}
{{< /tabs >}}

### Example 3:Single element
------------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R 
check_element_text(html = html, css = "t")
```
[1] "Beat COVID-19!"       "Dumpling YYDS!"       "Let's romantic!"     "Sweet Dumpling YYDS!"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R 
check_element_text(html = html, xpath = "//t")
```
[1] "Beat COVID-19!"       "Dumpling YYDS!"       "Let's romantic!"     "Sweet Dumpling YYDS!"

{{% /tabs %}}
{{< /tabs >}}

### Example 4:Multiple element
--------------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R 
check_element_text(html = html, css = "t, price")
```
[1] "Beat COVID-19!"       "1000000000.00"        
[3] "Dumpling YYDS!"       "100.00"
[5] "Let's romantic!"      "1000.0"              
[7] "Sweet Dumpling YYDS!" "100.0"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R 
check_element_text(html = html, xpath = "//t | //price")
```
[1] "Beat COVID-19!"       "1000000000.00"        
[3] "Dumpling YYDS!"       "100.00"
[5] "Let's romantic!"      "1000.0"              
[7] "Sweet Dumpling YYDS!" "100.0"

{{% /tabs %}}
{{< /tabs >}}

### Example 5:Position
------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R
check_element_text(html = html, css = "div:first-of-type")
```
[1] "Welcome 2022!    Beat COVID-19! 1000000000.00"

```R
check_element_text(html = html, css = "div:nth-of-type(2)")
```
[1] "Happy Spring Festival!     Dumpling YYDS! 100.00"

```R
check_element_text(html = html, css = "div:last-of-type")
```
[1] "Happy Valentine's Day!     Let's romantic! 1000.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 100.0"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R
check_element_text(html = html, xpath = "//div[position()=1]")
```
[1] "Welcome 2022!    Beat COVID-19! 1000000000.00"

```R
check_element_text(html = html, xpath = "//div[2]")
```
[1] "Happy Spring Festival!     Dumpling YYDS! 100.00"

```R
check_element_text(html = html, xpath = "//div[last()]")
```
[1] "Happy Valentine's Day!     Let's romantic! 1000.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 100.0"

{{% /tabs %}}
{{< /tabs >}}

### Example 6:ID attribute
----------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R
check_element_text(html = html, css = "div#div2")
```
[1] "Happy Spring Festival!     Dumpling YYDS! 100.00"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R
check_element_text(html = html, xpath = "//div[@id='div2']")
```
[1] "Happy Spring Festival!     Dumpling YYDS! 100.00"

{{% /tabs %}}
{{< /tabs >}}

### Example 7:Class attribute
-------------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R
check_element_text(html = html, css = "div.class1")
```
[1] "Welcome 2022!    Beat COVID-19! 1000000000.00"                                                              
[2] "Happy Valentine's Day!     Let's romantic! 1000.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 100.0"

```R
check_element_text(html = html, css = "div.class1.class2")
```
[1] "Happy Valentine's Day!     Let's romantic! 1000.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 100.0"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R
check_element_text(html = html, xpath = "//div[@class='class1']")
```
[1] "Welcome 2022!    Beat COVID-19! 1000000000.00"

```R
check_element_text(html = html, xpath = "//div[@class='class1 class2']")
```
[1] "Happy Valentine's Day!     Let's romantic! 1000.0    Happy Lantern Festival!     Sweet Dumpling YYDS! 100.0"

{{% /tabs %}}
{{< /tabs >}}

### Example 8:Asterisk
------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R
check_element_text(html = html, css = "*.class3")
```
[1] "Welcome 2022!    Beat COVID-19! 1000000000.00"    
[2] "Happy Spring Festival!     Dumpling YYDS! 100.00" 
[3] "Happy Valentine's Day!     Let's romantic! 1000.0"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R
check_element_text(html = html, xpath = "//*[@class='class3']")
```
[1] "Welcome 2022!    Beat COVID-19! 1000000000.00"    
[2] "Happy Spring Festival!     Dumpling YYDS! 100.00" 
[3] "Happy Valentine's Day!     Let's romantic! 1000.0"

{{% /tabs %}}
{{< /tabs >}}

### Example 9:Relationship
----------------------

{{< tabs >}}
{{% tab name="css selector" %}}

```R
check_element_text(html = html, css = "div#div2 t")
```
[1] "Dumpling YYDS!"

{{% /tabs %}}
{{% tab name="xpath" %}}

```R
check_element_text(html = html, xpath = "//div[@id='div2']/descendant::t")
```
[1] "Dumpling YYDS!"

```R
check_element_text(html = html, xpath = "//t[@class='text1']/ancestor::div")
```
[1] "Welcome 2022!    Beat COVID-19! 1000000000.00"                                                              

{{% /tabs %}}
{{< /tabs >}}

### Example 10:Calculation
----------------------

{{< tabs >}}
{{% tab name="css selector" %}}

Not avaiable

{{% /tabs %}}
{{% tab name="xpath" %}}

```R
check_element_text(html = html, xpath = "//p[price>50.0]/t")
```
[1] "Beat COVID-19!"       "Dumpling YYDS!"       "Let's romantic!"     "Sweet Dumpling YYDS!"

{{% /tabs %}}
{{< /tabs >}}
