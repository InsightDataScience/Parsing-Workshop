# Chapter 4: CAP files

In this chapter, we will discuss how to analyze capture files with Bash and Python. Capture files contain packets collected by a packet sniffing program and are also often called trace files or bone files.

We added  sample capture file `http.cap` which is originally from [here](https://wiki.wireshark.org/SampleCaptures#TCP).

## Bash

While not a Bash tool per se, many Bash scripts dealing with `cap` files use `tcpdump`, a software that can be used to filter and manipulate packages, store them in `cap` files and read old files. We will only use it to read old files, but feel free to look [here](https://linuxtechlab.com/learn-use-tcpdump-command-examples/) to learn more.

To get us started, execute the commands

```
 tcpdump -r http.cap
```
You should now see all packet contained in the file.

### Exercises
- Print all lines containing the IP address `65.208.228.223`.
- Compute the average time (in ms) between two packets in the file.

## Python

In Python, a popular package for working capture files is `pyshark`, which is based on `wireshark`.

### Installation
 - Make sure you install `wireshark` first
   - Mac OS X: `brew install wireshark`
   - Ubuntu:  `apt-get install wireshark`
 - You can then install pyshark via `pip install pyshark`

Here is a code snippet that reads the file and then walks through every packet to print out the timestamp:

```python
import pyshark
cap = pyshark.FileCapture('http.cap')

print(dir(cap)) # Prints all the fields that can be accessed

for packet in cap:          # Loops through every packet captured
  print(packet.sniff_time)  # Prints out the timestamp of the packet
```

To learn more about pyshark, read [here](https://kiminewt.github.io/pyshark/) for more details.

### Exercises

Please complete the same exercises in Python.

- Print all lines containing the IP address `65.208.228.223`.
- Compute the average time (in ms) between two packets in the file.


## Additional Exercises

- [Network Traffic](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/exercises/network_traffic)

## Next Chapter
Let us move on to [chapter 5](https://github.com/InsightDataScience/Parsing-Workshop/tree/master/chapter5).
