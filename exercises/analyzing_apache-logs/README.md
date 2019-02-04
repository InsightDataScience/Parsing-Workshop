# Analyzing Apache Logs

In this exercise, we will look at log files from an apache server (see apache_logs.txt in this folder). These logs are obtained from [Elastic's GitHub repository](https://github.com/elastic/examples/tree/master/Common%20Data%20Formats/apache_logs).

Entries in the log file have the following shape:

```
123.125.71.35 - - [17/May/2015:10:05:46 +0000] "GET /blog/tags/release HTTP/1.1" 200 40693 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)"
110.136.166.128 - - [17/May/2015:10:05:08 +0000] "GET /images/web/2009/banner.png HTTP/1.1" 200 52315 "http://www.semicomplete.com/style2.css" "Mozilla/5.0 (Windows NT 6.2; WOW64; rv:28.0) Gecko/20100101 Firefox/28.0"
50.150.204.184 - - [17/May/2015:10:05:46 +0000] "GET /images/googledotcom.png HTTP/1.1" 200 65748 "http://www.google.com/search?q=https//:google.com&source=lnms&tbm=isch&sa=X&ei=4-r8UvDrKZOgkQe7x4CICw&ved=0CAkQ_AUoAA&biw=320&bih=441" "Mozilla/5.0 (Linux; U; Android 4.0.4; en-us; LG-MS770 Build/IMM76I) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30"
207.241.237.225 - - [17/May/2015:10:05:58 +0000] "GET /blog/tags/examples HTTP/1.0" 200 9208 "http://www.semicomplete.com/blog/tags/C" "Mozilla/5.0 (compatible; archive.org_bot +http://www.archive.org/details/archive.org_bot)"
200.49.190.101 - - [17/May/2015:10:05:36 +0000] "GET /reset.css HTTP/1.1" 200 1015 "-" "-"
```

Your goal is to extract various analytics from this log that could help when troubleshooting.

## Exercises

1. Surface statistics of HTTP response codes: What percentage of requests return code 200, 400 etc?
2. Similarly, surface statistics on what kind of browsers tried to access the website.
3. What is the average number of requests per day?
4. You implemented a rating feature on the website and users rate the website significantly worse between 6pm and 9pm. Your boss thinks this is because there are more users during those hours which slows down the response time. Evaluate whether

   - This timeframe actually experiences most users.
   - The response time is actually slower during this timeframe.
