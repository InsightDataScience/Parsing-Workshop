# Chapter 5: Parsing HTML

In this chapter, we will learn how to write scripts that parse HTML files on the web and extract useful information. Before we dive into working with HTML files, let us quickly review what they typically look like.

Let us jump right into looking into a basic example
```html
<!DOCTYPE html>  
<html>  
    <head>
      <title>I am a first example</title>
    </head>
    <body>
        <h1> Hello World </h1>
        <p> Here is a paragraph </p>
        <p> Here is a another one!</p>
    <body>
</html>
```

HTML code consists of nested tags of form `<tag> content </tag>` (There are special tags that need not be closed). For example, the `<h1>` tag indicates that the content within is a header, whereas the `<p>` tag encloses a paragraph.

You can find this file in `hello.html`, open it with your browser to see the following output.

![hello.html](hello_screen.png)

The goal of HTML parsing is to extract content from these files. For instance, we could ask to extract all texts



## Bash

## Python

BeautifulSoup

## Exercises

## Additional Exercise
- [Weather Forecast](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/weather_forecast)
