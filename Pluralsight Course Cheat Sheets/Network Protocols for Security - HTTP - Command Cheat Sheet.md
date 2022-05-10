# Network Protocols for Security - HTTP - Cheat Sheet

**Pluralsight Lab:** [Network Protocols for Security - HTTP](https://app.pluralsight.com/labs/detail/c72816ed-0857-481e-aaee-9ed24f94d285/toc)

## Linux Reference
`cut` command options:

| Flag | Description                  |
| ---- | ---------------------------- |
| -f   | Specifies the field (column) |
| -d   | Specifies the delimiter      | 

"Sort Sandwich":
- `sort | uniq -c | sort -n`

## Apache access.log Filtering
Filter for a specific HTTP method:
- `cat ~/access.log | grep "OPTIONS"`

Filter and sort HTTP methods:
- `cat access.log | cut -f 6 -d " " | sort | uniq -c | sort -n`
- Field 6 = Method
- Field 7 = Resource
- Field 9 = Status Code

Filter and extract relevant fields to find out what data is being sent (POST) to the server:
- `cat ~/access.log | cut -f 1,6,7,9 -d " " | sort | uniq -c | sort -n | grep "POST"`

## Wireshark
Capture filter for specific ports:
- `port 80 or port 8000 or port 8080`

Display filter for HTTP User Agents:
`http.user_agent`

Add a field as a column:
- `Right Click a field -> Apply as Column`

Follow HTTP Stream:
- `Right Click a packet -> Follow -> HTTP Stream`

## Python Simple Server
Start a web server hosted on port 443 (will host any files in the current directory):
- `sudo python3 -m http.server 443`

Download a file using curl:
- `curl http://172.31.24.10:443/payload.txt -o payload.txt`


