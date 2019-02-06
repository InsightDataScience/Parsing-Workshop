# Computing Schedule Reports

In this exercise, we are working with text files containing schedules of multiple days, for each day, a schedule looks like

```
09:20 Breakfast Presidio
10:00 Exercises Ballard
11:15 Break
12:00 Workshop Capitol Hill
12:30 Lunch Break
13:30 Exercises North Beach
14:05 Discussion Flatiron
14:45 Break
14:55 Panel Presidio
15:40 Discussion Presidio
17:00 Solutions Flatiron
18:30 End
```

where `09:20 Breakfast Presidio` means that breakfast will start at 9:20 in the room Presidio.
You may assume the following about the data

- An event is scheduled until the start of the next event
- All events except for `Break`, `Lunch Break` and `End` have an assigned room
- Each day ends with an `End event`
- Room names may contain whitespaces, event names do not.

See example.txt in this folder for an example file.

## Exercises

1. For each event except for `End` events, add the end time, e.g. the first line in the example above should read `09:20-10:00 Breakfast Presidio`.
2. Compute the total number of minutes each event type occupies over all days, e.g. your output should have one line for each event type: `Exercises 20 minutes`.
3. Repeat exercise 2 with respect to each room.
4. In addition to the total number of minutes, output the percentage of time for each event type, e.g. `Exercises 20 minutes 12%`.
5. Repeat exercise 4 with respect to reach room.
6. Combine all of the above! Given an input file containing only one day as above, the output should look (the stats are not correct):
```
09:20-10:00 Breakfast Presidio
10:00-11:15 Exercises Ballard
11:15-12:00 Break
12:00-12:20 Workshop Capitol Hill
12:30-13:30 Lunch Ballard
13:30-14:05 Exercises North Beach
14:05-14:45 Discussion Flatiron
14:45-14:55 Break
14:55-15:40 Panel Presidio
15:40-17:00 Discussion Presidio
17:00-18:30 Solutions Flatiron
18:30 End

Breakfast 40 minutes 5.0%
Exercises 110 minutes 12.5%
Break 55 minutes 6%
Workshop 20 minutes 2%
Lunch 60 minutes 7%
Discussion 120 minutes 13%
Solutions 90 minutes 10.3%

Presidio 55 minutes 4%
Ballard 120 minutes 10%
Capitol Hill 300 minutes 24%
North Beach 220 minutes 19%
Flatiron 130 minutes 13%
```
