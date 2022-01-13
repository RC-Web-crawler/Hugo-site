+++
title = "Demo: Web Scraping with R/Python"
menuTitle = "4. Demo: with R & Python"
weight = 4
+++

***

#### Pre-prepare: Include packages that we need
{{< tabs groupId="include_packages">}}
{{% tab name="python" %}}
```python
from bs4 import BeautifulSoup # beautifulsoup4
import requests
import pandas as pd
import numpy as np
import re
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}


{{% notice note %}}
Within Novartis, we need proxy to get into some websites.
{{% /notice %}}
  

#### Pre-prepare: Interact with the website
{{< tabs groupId="read_in_the_url">}}
{{% tab name="python" %}}
```python
url = "https://www.lexjansen.com"
proxyDict = {'https': 'http://na-useh-proxy.na.novartis.net:2011'}
# Interact with data via a REST API
# Returns a <response> object
r = requests.get(url, proxies=proxyDict, verify=False)

# for css selector
soup = BeautifulSoup(r.text, 'lxml')

# for XPath
tree = html.fromstring(r.content)  
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}

Different parsers:
- 'lxml', 'html.parser', 'xml'...
- If it is a perfectly-formed HTML document, small differences between parsers.
- If the document is not perfectly-formed, different parsers give different results.

{{%expand "HTML file" %}}
```html
<!DOCTYPE html>
<!--[if lt IE 7]>      <html class="no-js lt-ie9 lt-ie8 lt-ie7" lang="en"> <![endif]--><!--[if IE 7]>         <html class="no-js lt-ie9 lt-ie8" lang="en"> <![endif]--><!--[if IE 8]>         <html class="no-js lt-ie9" lang="en"> <![endif]--><!--[if gt IE 8]>      <html class="no-js" lang="en"> <![endif]--><html><head>
<meta charset="utf-8"/>
<meta content="IE=edge" http-equiv="X-UA-Compatible"/>
<link href="https://fonts.googleapis.com/css?family=Special+Elite&amp;v1" rel="stylesheet" type="text/css"/>
<meta content="-gdlTJkYvyNRwnnZSHmM94zhCJNRmCwBfdNWk5u2yII" name="google-site-verification"/>
<meta content="c2f6e02546ad6b1a" name="yandex-verification"/>
<meta content="telephone=no" name="format-detection"/>
<meta content="none" name="msapplication-config"/>
<meta content="SAS Proceedings and more: Fortune Records, Dave Marsh 1001, ..." name="description"/>
<meta content="SAS Proceedings, Lex Jansen, Fortune Records, The Heart of Rock and Soul, Dave Marsh 1001" name="KeyWords"/>
<title>SAS Proceedings and more</title>
<script type="application/ld+json">{"@context":"https:\/\/schema.org","@type":"WebSite","url":"https:\/\/www.lexjansen.com\/","name":"Lex Jansen's Homepage"}</script>
<script type="application/ld+json">{"@context":"https:\/\/schema.org","@type":"Person","url":"https:\/\/www.lexjansen.com\/",
    "sameAs":["https:\/\/instagram.com\/lex.jansen\/","https:\/\/www.evernote.com\/pub\/lexjansen\/public","https:\/\/www.linkedin.com\/in\/lexjansen","https:\/\/plus.google.com\/u\/0\/+LexJansen","https:\/\/www.youtube.com\/user\/lexjansen","https:\/\/twitter.com\/lexjansen"],"name":"Lex jansen"}</script>
<link href="favicon.ico" rel="icon" type="image/x-icon"/>
<link href="favicon.ico" rel="shortcut icon" type="image/x-icon"/>
<link href="/apple-touch-icon.png" rel="apple-touch-icon"/>
<link href="/apple-touch-icon-57x57.png" rel="apple-touch-icon" sizes="57x57"/>
...
<br/>
Copyright © 1999-2022 Lex Jansen. All rights reserved.<br/>
SAS is a registered trademark of SAS Institute Inc.
SAS, Statistical Analysis System, and all other SAS Institute Inc. product or service names are registered trademarks or trademarks of SAS Institute Inc. in the USA and other countries. ® indicates USA registration.
</div>
<script src="https://www.google-analytics.com/urchin.js" type="text/javascript"></script>
<script type="text/javascript"> _uacct = "UA-132232-1"; urchinTracker();</script>
<script async="" data-goatcounter="https://lexjansen.goatcounter.com/count" src="//gc.zgo.at/count.js"></script>
<script type="text/javascript">
    var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "https://www.");
    document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
  </script>
<script type="text/javascript">
    var pageTracker = _gat._getTracker("UA-132232-1");
    pageTracker._trackPageview();
  </script>
</div>
</body>
</html>
```
{{% /expand%}}

#### Structure
{{<mermaid align="center">}}
graph TB;
    A[Title, Link, Author, Keyword, Pages, Size]
    B[Conference name, Conference place, Conference time]
    C[Section name, Best paper flag]
    F[Final dataset]
    A --> F
    B --> F        
    C --> F
    subgraph g1 [Paper information]
    A
    end
    subgraph g2[Conference information]
    B
    end
    subgraph g3[Paper attributes]
    C
    end
{{< /mermaid >}}

#### One example that we use
| Paper information |
| ------ | -----|
| Title  | A Case Study of Mining Social Media Data for Disaster Relief: Hurricane Irma|
| Link   | https://www.sas.com/content/dam/SAS/support/en/sas-global-forum-proceedings/2018/2695-2018.pdf |
| Author | Bogdan Gadidov, Linh Le |
| Keyword| Text Mining Topic Modeling Time Series |
| Pages  | 11 |
| Sizes  | 660 kb |

| Conference information |
| ------ | -------|
| Conference name | SAS Global Forum 2018 |
| Conference place| Denver, Colorado |
| Conference time | April 8-11, 2018 |

| Paper attributes|
| ------ | -------|
| Section name    | Breakout |
| Best paper flag |  |


#### 1. Homepage -> Get the SUGI url
{{<mermaid align="center">}}
graph LR;
    A["div id='sasproceedings'"] --> B[ul]
    B --> C[li];
    C --> D["div class='pf'"];
    D --> E[div];
    E --> F[span] --> G[a];
    style G fill:#f3d7d3;
{{< /mermaid >}}

`<a href="/sugi">SUGI / SAS Global Forum</a> papers (1976-2021)`

{{< tabs groupId="sugi_url">}}
{{% tab name="python" %}}
```python
# CSS selector
soup.select("div[id = 'sasproceedings'] > ul > li > div > div > span > a")
soup.select("div[id = 'sasproceedings'] a")

# XPath
tree.xpath('//div[@id ="sasproceedings"]/ul/li/div/div/span/a/text()')
tree.xpath('//div[@id ="sasproceedings"]/descendant::a/text()')

# Get SUGI URL
href = soup.select("div[id = 'sasproceedings'] a")[5].get('href')
sugi_url = url + href
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}

#### 2. SUGI / SAS Global Forum -> Get conference information
{{<mermaid align="center">}}
graph LR;
    A["ul class='conferences'"] --> B["li class='conference'"]
    B --> C[a];
    B --> D[span];
    B --> E[span];
    style C fill:#f3d7d3;
    style D fill:#f3d7d3;
    style E fill:#f3d7d3;
{{< /mermaid >}}
`<a href="../cgi-bin/xsl_transform.php?x=sgf2018">SAS Global Forum 2018</a>`     
`<span>April 8-11, 2018</span>`     
`<span>Denver, Colorado</span>`   

{{< tabs groupId="sugi_sas">}}
{{% tab name="python" %}}
```python
r_sugi = requests.get(sugi_url, proxies=proxyDict, verify=False)
soup2 = BeautifulSoup(r_sugi.text, 'lxml')
tree2 = html.fromstring(r_sugi.content)  

# SUGI Forun 2018 url
soup2.select('li a')[3].get('href')
sugi_2018_url = url + soup2.select('li a')[3].get('href')[2:]

# 1. conference name
# CSS selector
soup2.select("li a")[3].text
# XPath
tree2.xpath('//li/a/text()')[3]

# 2. conference time
# CSS selector
soup2.select("li[class = 'conference']")[3].select("span")[0].text
# XPath: first <span> element under <li>
tree2.xpath('//li/span[1]/text()')[3]

# 3. conference place
# CSS selector
soup2.select("li[class = 'conference']")[3].select("span")[1].text
# XPath: second <span> element under <li>
tree2.xpath('//li/span[2]/text()')[3]
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}


#### 3. SUGI Forum 2018 webpage -> Get paper information
{{< tabs groupId="info">}}
{{% tab name="python" %}}
```python
# create soup3 & tree3
r_sugi_2018 = requests.get(sugi_2018_url, proxies=proxyDict, verify=False)
soup3 = BeautifulSoup(r_sugi_2018.text, 'lxml')
tree3 = html.fromstring(r_sugi_2018.content)  
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}
{{<mermaid align="center">}}
graph LR;
    A["div class='paper bl'"] --> B["a id='sgf2018.2659-2018'"];
    A --> C["span class='code'"];
    A --> D["a target='_blank'"  Title & Link];
    style D fill:#f3d7d3;
    A --> E["img class='download'"];
    A --> F[a, Author];
    A --> G[a, Author];
    style F fill:#f3d7d3; 
    style G fill:#f3d7d3; 
    A --> H["span class='key'", keyword] -->I[b];
    style H fill:#f3d7d3; 
    A --> J["span class='size'", Pages] -->j[b];
    A --> K["span xmlns:gcse='uri:dummy-google-ns' class='size'", Size] -->k[b];
    style J fill:#f3d7d3; 
    style K fill:#f3d7d3; 
{{< /mermaid >}}
`Title`: Under `<a taget="_blank">` tag    
`<a target="_blank" href="https://www.sas.com/content/dam/SAS/support/en/sas-global-forum-proceedings/2018/2695-2018.pdf"`    
`>A Case Study of Mining Social Media Data for Disaster Relief: Hurricane Irma</a>`   
{{< tabs groupId="title">}}
{{% tab name="python" %}}
```python
# CSS selector
soup3.select('div.paper > a[target = "_blank"]')[2].text
# XPath: find the second <a> element, which is the child of div.paper.wh
tree3.xpath('//div[contains(@class, "paper")]/child::a[2]/text()')[2]
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}


`Link`
{{< tabs groupId="link">}}
{{% tab name="python" %}}
```python
# CSS selector
soup3.select('div.paper > a[target = "_blank"]')[2].get('href')
# XPath:
tree3.xpath('//div[contains(@class, "paper")]/child::a[2]/@href')[2]
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}


`Author`: Under `<a>` tag   
`<a href="/cgi-bin/xsl_transform.php?x=ag&amp;c=SUGI#bogdidov">Bogdan Gadidov</a>`  
`<a href="/cgi-bin/xsl_transform.php?x=al&amp;c=SUGI#linhnhle">Linh Le</a>`
{{< tabs groupId="author">}}
{{% tab name="python" %}}
```python
# beautifulsoup syntax
soup3.find_all("div", {"class": "paper"})[2].find_all('a', id=None, target=None)
# XPath: within the <div>, with attribute contains "paper", find <a> tag without attributes "id" and "target"
tree3.xpath('//div[contains(@class, "paper")][3]/a[not(@id) and not(@target)]/text()')
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}


`Keyword`: Under `<span>` tag   
`<span class="key"><b>Keywords:</b> Text Mining Topic Modeling Time Series </span>`
{{< tabs groupId="keyword">}}
{{% tab name="python" %}}
```python
# CSS selector
soup3.select('div.paper > span[class = "key"]')[0].text
# XPath: within the <div>, with attribute contains "paper", find the <span> tag with attribute class="key"
tree3.xpath('//div[contains(@class, "paper")][3]/span[@class = "key"]/text()')
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}

`Pages & Size`: Under `<span>` tag     
`<span class="size"><b>Pages</b>:&nbsp;11&nbsp;</span>`  
`<span xmlns:gcse="uri:dummy-google-ns" class="size"><b>Size</b>:&nbsp;660&nbsp;Kb&nbsp;</span>`   

{{< tabs groupId="ps">}}
{{% tab name="python" %}}
```python
# CSS selector
soup3.select('div.paper')[2].select('span[class = "size"]')
# XPath: within the <div>, with attribute contains "paper", find the <span> tag with attribute class="size"
tree3.xpath('//div[contains(@class, "paper")][3]/span[@class = "size"]/text()')
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}


{{%expand "Grab paper information (Title, Link, Author, Keyword, Pages, Sizes) from one conference" %}}
```python
def one_conf(url):
    r_sugi = requests.get(url, proxies=proxyDict, verify=False)
    soup = BeautifulSoup(r_sugi.text, 'lxml')
    num_paper = len(soup.select('div.paper'))
    
    title = []
    link = []
    author = []
    keyword = []
    page = []
    size = []
    
    for i in range(num_paper):
        div = soup.find_all("div", {"class": "paper"})[i]
        # title & link
        tl = div.select('div.paper > a[target = "_blank"]')
        if not tl: # tl is empty
            if div.find("span", {"class": "code"}) is not None:
                t_new = div.find("span", {"class": "code"}).findNextSibling(text=True)
            else:
                t_new = div.find("a").findNextSibling(text=True)
            title.append(t_new)
            link.append("")
            tag = div.select('div > a')[1:]
            ps = []
        else:
            title.append(tl[0].text)
            link.append(tl[0].get('href'))
            tag = div.select('div > a')[2:]
            ps = div.find_all("span", {"class": "size"})
        
        # author
        author2 = []
        for j in range(len(tag)):
            author2.append(tag[j].text)
        author.append(author2)
        
        # keyword
        key = div.find("span", {"class": "key"})
        if key is None:
            keyword.append("")
        else:
            keyword.append(key.text[10:])
        
        # page & size
        if len(ps) >= 2:
            p = ps[0]
            s = ps[1]
            if p is not None and s is not None:
                if 'Page' in p.text:
                    p2 = re.search('\xa0(.*)\xa0', p.text)
                    page.append(p2.group(1))
                    if 'Size' in s.text:
                        s2_r = re.search('\xa0(.*)\xa0(.*)\xa0', s.text)
                        s2 = s2_r.group(1) + " " + s2_r.group(2)
                        size.append(s2)
                    else:
                        size.append("")
                elif 'Size' in p.text:
                    s2_r = re.search('\xa0(.*)\xa0(.*)\xa0', p.text)
                    s2 = s2_r.group(1) + " " + s2_r.group(2)
                    size.append(s2)
                    page.append("")
            else:
                size.append("")
                page.append("")
                
        elif len(ps) == 1:
            p = ps[0]
            if 'Page' in p.text:
                p2 = re.search('\xa0(.*)\xa0', p.text)
                page.append(p2.group(1))
                size.append("")
            elif 'Size' in p.text:
                s2_r = re.search('\xa0(.*)\xa0(.*)\xa0', p.text)
                if s2_r is not None:
                    s2 = s2_r.group(1) + " " + s2_r.group(2)
                    size.append(s2)
                    page.append("")
                else:
                    page.append("")
                    size.append("")
            else:
                page.append("")
                size.append("")
        else:
            page.append("")
            size.append("")
            
        
    # derive dataframe
    dataset = pd.DataFrame({'Title'  : title,
                            'Keyword': keyword,
                            'Link'   : link,
                            'Author' : author,
                            'Pages'  : page,
                            'Size'   : size})
    dataset['Author'] = [", ".join(n) for n in dataset['Author']]
    return dataset
```
{{% /expand%}}

{{%expand "Grab conference information (Conference place & time & name) from all conferences" %}}
```python
def all_paper(url):
    global conf_name, conf_time, conf_place
    r_sugi = requests.get(url, proxies=proxyDict, verify=False)
    soup = BeautifulSoup(r_sugi.text, 'lxml')
    
    num_paper = len(soup.select("li a"))
    df_list = []
    for i in range(num_paper):
        # print(i)
        conf_name = soup.select("li a")[i].text
        conf_time = soup.select("li > span")[2*i].text
        conf_place = soup.select("li > span")[2*i+1].text
        
        conf_url = 'https://www.lexjansen.com' + soup.select('li a')[i].get('href')[2:]
        df = one_conf(conf_url)
        df.insert(column = "Conference_place", value = conf_place, loc=0)
        df.insert(column = "Conference_time", value = conf_time, loc=0)
        df.insert(column = "Conference_name", value = conf_name, loc=0)
        
        df_list.append(df)
    return df_list

conf = all_paper('https://www.lexjansen.com/sugi')
SUGI = pd.concat([pd.DataFrame(conf[x]) for x in range(num_paper)], axis = 0, ignore_index=True)
SUGI.to_csv('SUGI.csv', index = False)
```
{{% /expand%}}

{{<mermaid align="center">}}
graph TB;
    A[Title, Link, Author, Keyword, Pages, Size]
    B[Conference name, Conference place, Conference time]
    C[Section name, Best paper flag]
    F[One conference]
    G[One forum]
    A --grab from 468 papers--> F
    F --grab from 46 conferences--> G
    B --merge conference's info -->F
    C --merge paper attributes -->G
    subgraph g1 [One paper's info]
    A
    end
    subgraph g2[Conference information]
    B
    end
    subgraph g3[Paper attributes]
    C
    end
{{< /mermaid >}}

#### 4. Get paper attributes: Section name
Only grab section name & title from the url
```python
def title_grab(url):
    r_sugi = requests.get(url, proxies=proxyDict, verify=False)
    soup = BeautifulSoup(r_sugi.text, 'lxml')
    num_paper = len(soup.select('div.paper'))
    
    title = []
    
    for i in range(num_paper):
        div = soup.find_all("div", {"class": "paper"})[i]
        # print(i)
        t = div.find("a").findNextSibling()
        if not t:
            print("No title")
        else:
            title.append(t.text)
    title_df = pd.DataFrame({'Title'  : title})
    return title_df

def section_grab(url):
    s = requests.get(url, proxies=proxyDict, verify=False)
    soup = BeautifulSoup(s.text, 'lxml')
    num_stream = len(soup.select("div[class='streams'] span"))
    
    df_list = []
    for i in range(num_stream):
        # print(i)
        x = soup.find_all("span", {"class": "stream"})[i]
        sec_name = x.text        
        sec_url = 'https://www.lexjansen.com' + x.find("a").get('href')[2:]
        df = title_grab(sec_url)
        df.insert(column = "Section_name", value = sec_name, loc=0)        
        df_list.append(df)
    return df_list

section = section_grab("https://www.lexjansen.com/sugi/")
Sections = pd.concat([pd.DataFrame(section[x]) for x in range(num_section)], axis = 0, ignore_index=True)
Sections.to_csv('Sections.csv', index = False)
```

#### 5. Merge section names back to the origin file
```python
sugi = pd.read_excel('SUGI.xlsx')  
section = pd.read_excel('Sections.xlsx')  
pd.merge(sugi, section, on="Title", how='left')
```

#### 6. Get paper attributes: Best paper flag
Only grab the title from the url, and provide "Y" to column "Best_paper_fl"
```python
def best_paper_title(url):
    r_sugi = requests.get(url, proxies=proxyDict, verify=False)
    soup = BeautifulSoup(r_sugi.text, 'lxml')
    title = []
    best = soup.select("div.paperback > a")
    if best:
        for pp in best:
            title.append(pp.text)
    paper_df = pd.DataFrame({'Title'  : title})
    return paper_df

def best_paper_fl(url):
    r_sugi = requests.get(url, proxies=proxyDict, verify=False)
    soup = BeautifulSoup(r_sugi.text, 'lxml')
    paper = soup.select("li a")
    df_list = []
    for i in range(len(paper)):
        # print(i)
        conf_url = 'https://www.lexjansen.com' + paper[i].get('href')[2:]
        df = best_paper_title(conf_url)
        df.insert(column = "Best_paper_fl", value = "Y", loc=0)   
        df_list.append(df)
    return df_list

best = best_paper_fl("https://www.lexjansen.com/sugi/")
best = pd.concat([pd.DataFrame(best[x]) for x in range(46)], axis = 0, ignore_index=True)
best.to_csv('Best_paper.csv', index = False)
```

#### 7. Derive final dataset
{{< tabs groupId="final">}}
{{% tab name="python" %}}
```python
sugi = pd.read_excel('SUGI.xlsx')  
section = pd.read_excel('Sections.xlsx')  
best =  pd.read_excel('Best_paper.xlsx')  
final = sugi.merge(section, on='Title', how='left').merge(best, on='Title', how='left')
final.to_csv('SUGI_paper.csv', index = False)
```
{{% /tab %}}
{{% tab name="R" %}}
```R
library()
```
{{% /tab %}}
{{< /tabs >}}