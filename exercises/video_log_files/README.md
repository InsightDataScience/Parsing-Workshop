# Analyzing Video Log files

You are working at a company that hosts servers for video streaming.
The log files of the video server have the shape

```
video-id   user-id   start/stop         timestamp
A1         userid01    start      09/09/2018-11:55:40
A1         userid01    stop       09/09/2018-12:05:40
A1         userid01    start      09/09/2018-13:25:40
A1         userid01    stop       09/09/2018-14:40:40
B1         userid01    start      09/09/2018-14:40:41
A1         userid01    start      09/09/2018-15:55:40
B1         userid01    stop       09/09/2018-16:00:40
A1         userid01    stop       09/ 09/2018-16:05:40
A1         userid01    start      09/ 21/2018-11:55:40
```

and can be found in logs.txt.

A couple of notes on the log files:

- Two users can have the same video playing at the same time.
- Same user can be playing two different videos at the same time
- Videos can be played across dates
- You can assume each started video does have a stop timestamp

# Exercises

- Determine the top two most played videos during the days 9/21-9/22/2018.
- Determine the duration that the fourth most played video was played.
- Determine all users that have watched at least three videos simultaneously.
