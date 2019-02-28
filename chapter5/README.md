# Chapter 5: Parsing HTML

In this chapter, we will learn how to write scripts that parse HTML files on the web and extract useful information. Before we dive into working with HTML files, let us quickly review what they typically look like.

A basic example html file looks like
```html
<!DOCTYPE html>  
<html>  
    <head>
      <title>I am a first example</title>
    </head>
    <body>
        <h1> Hello World </h1>
        <p id="unique_identifier"> Here is a paragraph </p>
        <p> Here is a another one!</p>
    <body>
</html>
```

HTML code consists of nested tags of the form `<tag> content </tag>` (There are special tags that need not be closed). For example, the `<h1>` tag indicates that the content within is a header, whereas the `<p>` tag encloses a paragraph.

You can find this file in `hello.html`, open it with your browser to see the following output.

![hello.html](hello_screen.png)

The goal of HTML parsing is to extract content from these files. For instance, we could extract all texts within the `<h1>` tags to generate a rudimentary table of content.

Before we jump into parsing html files, let us discuss how we can analyze more complex html files. As an example, go to [weather.com](https://weather.com/), a website that does not look too complex at first glance.
Using your favorite web browser, view the sites source (in Chrome: right click and `View page source`).
You will see a huge mess of html code that is difficult to understand.
This where most modern browser's come in. On Google Chrome for instance, you can right click a particular object and click on `Inspect`.
If you do this for the `Today` button on the top of the page, you can see the corresponding HTML code containing the the text and the link of the button:

![Today](inspect.png)


### Exercise
- What is the `classname` of the `div` tag that contains the box entitled *Our Photo Gallery Picks*?

<details><summary>Show Solution</summary>
<p>
cm-small-content wx-media-group
</p>
</details>


## Bash

There are many different parsing tools available, we will first discuss (xpath)[https://www.w3schools.com/xml/xml_xpath.asp] here.
With xpath, you can provide a query using a *path expression* to return the nodes within the html document that you are interested in.

For instance, if you want to parse `hello.html` and extract all the nodes with the `<p>` tag, you can type the following:

```Bash
xpath hello.html '//h1'
```

If you want all `title` tags that are located within the `head` tag, you could use the following query:

```Bash
xpath hello.html '/html/head/title'
```

You can use this approach to find subnodes within any path, i.e. the query `/a/b/c/d` will find all `d` notes that live under the path `a/b/c`.

### Additional resources
- (xpath Cheatsheet)[https://devhints.io/xpath#prefixes]

While `xpath` goes a long way, it can be quite clunky when dealing with complex html files.

A powerful alternative is given by (pup)[https://github.com/ericchiang/pup]. Let us dive right into an example! If you execute

```
curl https://www.insightdevops.com | pup 'title'
```
you should get the following output:
```
<title>
 Insight DevOps Engineering Fellows Program
</title>
```

In general `pup 'element'` filters the html file for all nodes of type `element`. We can chain these filters conveniently:

```
cat hello.html | pup 'body p'
```

returns

```
<p id="unique_identifier">
 Here is a paragraph
</p>
<p>
 Here is a another one!
</p>
```

We can also specify the `id` using `#`:

```
cat hello.html | pup 'body p#unique_identifier'
```

returns

```
<p id="unique_identifier">
 Here is a paragraph
</p>
```

Similarly, `pup` allows us to filter for all kinds of attributes and also specify relative filters. For instance, to find all all parents of a `<p>` tag, you can execute

```
cat hello.html | pup ':parent-of(p)'
```
and should see

```
<body>
 <h1>
  Hello World
 </h1>
 <p id="unique_identifier">
  Here is a paragraph
 </p>
 <p>
  Here is a another one!
 </p>
</body>
```
### Additional resources

- The (Readme)[https://github.com/ericchiang/pup] provides a great resource to learn more about `pup`

## Python

There are many great resources for parsing html documents using Python. (BeautifulSoup)[https://www.crummy.com/software/BeautifulSoup/bs4/doc/] has emerged as one of the most popular and convenient tools for html parsing under Python.

There are many great resources on BeautifulSoup online, we like the one from DigitalOcean which explains syntax and concepts very cleanly.

### Action item

- Work through the excellent tutorial on BeautifulSoup on [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-scrape-web-pages-with-beautiful-soup-and-python-3)

## Exercises

- Let us the tackle the classic web scraping example: [Extract all article titles from the New York Times homepage](http://www.practicepython.org/exercise/2014/06/06/17-decode-a-web-page.html)!
- Be sure to solve the above exercise using Python and Bash.

## Additional Exercise
- [Weather Forecast](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/weather_forecast)
