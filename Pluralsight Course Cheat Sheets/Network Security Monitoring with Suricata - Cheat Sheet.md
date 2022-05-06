# Network Security Monitoring with Suricata - Command Cheat Sheet
Pluralsight Lab: [Network Security Monitoring with Suricata](https://app.pluralsight.com/labs/detail/5cb37490-9731-4c67-bb8f-6f0b7b5b9f8a/toc)

## Services
Check service status for Suricata and Evebox:
- `sudo systemctl status suricata.service evebox.service`

## eve.json Filtering
Filter for specific event types:
- `grep '"event_type":"http"' /var/log/suricata/eve.json | jq .`

Filter and extract out specific fields:
- `grep '"event_type":"alert"' /var/log/suricata/eve.json | jq '"\(.timestamp) | \(.alert.gid):\(.alert.signature_id):\(.alert.rev) | \(.alert.signature) | \(.alert.category) | \(.src_ip):\(.src_port) -> \(.dest_ip):\(.dest_port)"'`

## Rules
Sample rule:
- `alert icmp any any -> any any (msg: "TEST icmp packet found"; sid: 1; rev: 1;)`

Find a specific rule based on the Signature ID:
- `sudo grep "2021997" /var/lib/suricata/rules/suricata.rules`

## Extracting Portable Executables
Make configuration changes to /etc/suricata/suricata.yaml:
```yml
# File-store -> 
enabled: yes
Stream-depth: 0
# Under libhtp section: 
Response-body-limit: 0
```

Rule to extract Portable Executable (PE) Files:
- `alert http any any -> any any (msg:"PE File Extracted"; filestore; filemagic:"PE32 executable"; sid:100001; rev:1;)`
