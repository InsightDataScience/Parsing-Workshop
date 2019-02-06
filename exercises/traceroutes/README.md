# Analyzing Traceroutes

## Dataset

This data set consists of query results of [traceroutes](https://en.wikipedia.org/wiki/Traceroute) from 50 servers around the world to the top 20 websites as listed by Alexa.com in September 2007.

Within the directory PAM08, there is one folder for each of the 50 servers. Within each folder, there is an HTML doc for each of the top 20 websites. These html files contain the corresponding traceroutes.

For example, in the folder `Germany`, there is a file `Germany_www.youtube.com.html` that contains the traceroutes from YouTube and a webserver located in Germany. Within the html file, the traceroutes are stored in the format of:

```
trying to get source for 208.65.153.238
source should be 193.141.98.37
traceroute to 208.65.153.238 (208.65.153.238) from 193.141.98.37 (193.141.98.37), 30 hops max
outgoing MTU = 1500
 1  pophannover.helios.de (193.141.98.1)  3 ms  2 ms  2 ms
 2  popcore2.pop-hannover.net (62.48.66.117)  2 ms  2 ms  2 ms
 3  globalcore.pop-hannover.net (62.48.66.102)  2 ms  2 ms  2 ms
 4  dcxcore.pop-hannover.net (62.48.66.58)  9 ms  9 ms  9 ms
 5  decix.mpd01.fra03.atlas.cogentco.com (80.81.192.63)  51 ms  21 ms  20 ms
 6  t7-2.mpd01.par02.atlas.cogentco.com (130.117.0.102)  106 ms t4-2.mpd01.par02.atlas.cogentco.com (130.117.0.222)  100 ms  100 ms
 7  t2-2.mpd02.par01.atlas.cogentco.com (130.117.2.81)  20 ms  20 ms  20 ms
 8  * * *
 9  t8-3.mpd01.dca02.atlas.cogentco.com (154.54.6.198)  206 ms  226 ms  213 ms
10  v3494.mpd01.iad01.atlas.cogentco.com (154.54.5.42)  109 ms  108 ms  107 ms
11  38.101.184.202 (38.101.184.202)  99 ms  99 ms  99 ms
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  208.65.153.238 (208.65.153.238)  171 ms  170 ms  171 ms
```

More information on the dataset can be found [here](http://ita.ee.lbl.gov/html/contrib/gill-PAM08.html).

## Reading Traceroutes

The first part of the HTML is information about who is trying to connect to to whom: it shows the target system, that system's IP address, the maximum number of hops that will be allowed, and the size of the packets being sent.

We now see detailed listing of all the different routers that were encountered on our trip. Each line shows the name of the next system (via DNS), its ip address and three times: Those correspond to the round trip time in milliseconds.

An asterisk in a  line stands for a packet that the system did not respond to.

If you see a line with an IP address but no name such as

 ```
 4  217.26.159.20) (217.26.159.20)  0.228 ms  1.223 ms  0.543 ms
 ```

then the DNS lookup failed.

Lastly, your system may end in all timeouts:

```
11  38.101.184.202 (38.101.184.202)  99 ms  99 ms  99 ms
12  * * *
13  * * *
14  * * *
```

Then your packets never returned to their origin. It is unclear whether they made it to their destination.

A trace can end with one of several error indications indicating why the trace cannot proceed. In this example, the router is indicating that it has no route to the target host:


More information on reading traceroutes can be found [here](http://www.exit109.com/~jeremy/news/providers/traceroute.html).



## Exercises

1. Write a script that, for a given HTML file, determines the following:
    1. Was the traceroute successful?
    2. What was the average round trip time?
    3. How many hops were needed to complete the trip?
2. Write a script that goes through all HTML files to determine:
    1. Which server had the highest success rate?
    2. Which server had the shortest average round trip time?
    3. Which server had the lowest average number of hops?
3. Write a script that goes through all HTML files to determine:
    1. Which website had the highest success rate?
    2. Which website had the shortest median round trip time?
4. Write a script that goes through all HTML files to determine:
    1. Which webserver/website combo hat the shortest average round trip time?
