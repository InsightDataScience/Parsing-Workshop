# Network Traffic Analysis

In this exercise, we will play around with a packet capture (see `dns.cap` in this folder). The data and some of the exercises are taken from [AACC Cyber competition practice](https://cybercompaacc.com/challenges/network-traffic-analysis/traffic-analysis-1/).

We highly recommend to work on this exercise after having completed chapter 4 of the workshop where you learn on how to work with capture packets and `.cap` files in both Python and Bash.
It also gives an overview over DNS look ups and common DNS lookup types.

A typical record in `dns.cap` has the shape

```
00:49:35.461181 IP 192.168.170.8.32795 > 192.168.170.20.domain: 61652+ AAAA? www.netbsd.org. (32)
```

## Exercises
- What is the IP address of www.netbsd.org?
- For what domain was there a mail exchange lookup?
- Name a mail exchange server for google.com!
- For what domain was there a name server lookup?
- What is the reverse DNS of 66.192.9.104?
- Write a script that given a pairs all requests (i.e. request types ending with a `?`) paired with their responses.
