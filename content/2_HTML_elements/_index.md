+++
title = "HTML elements & Tree Structure"
menuTitle = "2. HTML elements"
weight = 2
+++

- [**2. HTML elements & Tree Structure**](#2-html-elements--tree-structure)
  - [**2.1 HTML elements**](#21-html-elements)
  - [**2.2 HTML Attributes**](#22-html-attributes)
  - [**2.3 Tree structure of HTML document**](#23-tree-structure-of-html-document)
    - [**2.3.1 Relationship of Nodes**](#231-relationship-of-nodes)

## **2. HTML elements & Tree Structure** 

### **2.1 HTML elements** 

An HTML element is defined by a **start tag**, **some content**, and an **end tag**. The HTML element is everything from the start tag to the end tag: 

`<tagname>Content goes here...</tagname>`

>*Examples:*  
`<h1>欢迎来到爬虫小组的网页！</h1>`   
`<p>这是一个简单的测试页 </p>`

|Start tag|Element content        |End tag|
|---------|-----------------------|-------|
|`<h1>`   |欢迎来到爬虫小组的网页   |`</h1>`|
|`<p>`    |这是一个简单的测试页     |`<p>`  |
|`<br>`   |*none*                 |*none* |

<span style="background-color:rgb(255, 246, 143);padding:3px 0px;font-family:Georgia"> **Note**: Some HTML elements have no content (like the `<br>` element). These elements are called empty elements. Empty elements do not have an end tag!</span>

**Common elements explained:**
>The `<!DOCTYPE html>` declaration defines that this document is an HTML5 document.<br>
The `<html>` element is the root element of an HTML page<br>
The `<head>` element contains meta information about the HTML page<br>
The `<title>` element specifies a title for the HTML page (which is shown in the browser's title bar or in the page's tab)<br>
The `<body>` element defines the document's body, and is a container for all the visible contents, such as headings, paragraphs, images, hyperlinks, tables, lists, etc.<br>
The `<h1><h2>` element defines a large heading<br>
The `<p>` element defines a paragraph

### **2.2 HTML Attributes**

HTML attributes provide additional information about HTML elements. All HTML elements can have attributes. Attributes are always specified in the **start tag**. Attributes usually come in name/value pairs like: **name="value"**.

- The ***href*** Attribute：<br> The `<a>` tag defines a hyperlink. The `href` attribute specifies the URL of the page the link goes to. <br>
 *Example*:<br> <span style="background-color:rgb(211,211,211);padding:3px 0px;font-family:Georgia;font-size:12px">
`<a href="http://gitlabce.apps.dit-prdocp.novartis.net/YUHAY/web-crawler-do.git">Web Crawler DO</a>`</span>

- The ***src*** Attribute：<br> The `<img>` tag is used to embed an image in an HTML page. The `src` attribute specifies the path to the image to be displayed. <br>
 *Example*:<br> <span style="background-color:rgb(211,211,211);padding:3px 0px;font-family:Georgia;font-size:13px">
`<img src="https://www.w3schools.com/js/pic_bulboff.gif">`</span>

- The ***style*** Attribute：<br> The `style` attribute is used to add styles to an element, such as color, font, size, and more. <br>
 *Example*:<br> <span style="background-color:rgb(211,211,211);padding:3px 0px;font-family:Georgia;font-size:13px">
`<img style="width:30px">`</span>

>The `width` and `height` attributes of `<img>` provide size information for images<br> 
The `alt` attribute of `<img>` provides an alternate text for an image<br> 
The `lang` attribute of the `<html>` tag declares the language of the Web page<br> 
The `title` attribute defines some extra information about an element

### **2.3 Tree structure of HTML document**

HTML documents can be treated as trees of nodes. Look at the following document:

```
<books>
  <book>
    <title lang="en">Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>
</books>
```
The topmost element of the tree is called the **root element**. `<books>` is the root element node of the above tree. There are other element nodes, such as `<author>J K. Rowling</author>`, `<year>2005</year>`, *etc*.

It also looks like the path of computer file systems:

<img src="https://www.w3schools.com/xml/img_xpath_folders.jpg">

#### **2.3.1 Relationship of Nodes**

*Example 1:*
```
<book>
  <title>Harry Potter</title>
  <author>J K. Rowling</author>
  <year>2005</year>
  <price>29.99</price>
</book>
```
**1. Parent**

Each element has one parent.

In the example 1; the `book` element is the parent of the `title`, `author`, `year`, and `price`.

**2. Children**

Element nodes may have zero, one or more children.

In the example 1; the `title`, `author`, `year`, and `price` elements are all children of the `book` element.

**3. Siblings**

Nodes that have the same parent.

In the example 1; the `title`, `author`, `year`, and `price` elements are all siblings.

*Example 2:*
```
<books>

  <book>
    <title>Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>

</books>
```

**4. Ancestors**

A node's parent, parent's parent, etc.

In the example 2; the ancestors of the `title` element are the `book` element and the `books` element.

**5. Descendants**

A node's children, children's children, etc.

In the example 2; descendants of the `books` element are the `book`, `title`, `author`, `year`, and `price` elements.