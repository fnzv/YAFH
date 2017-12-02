## Yet Another Fake Honeypot

### Quickstart

1) Clone repo locally<br>
```git clone https://github.com/fnzv/YAFH.git && cd YAFH```
2) Build and create Go binaries <br>
```go build yafh.go```
3) Execute the Honeypot: <br>
```./yafh```
<br><br>
- All users trying to connecting via TELNET to port 23 will be shown a fake CISCO router login <br>
- All the actions executed by malicious users will be saved into yafh.log, (same dir where you started the binary file) <br><br>

Tested on Ubuntu 16.04
<br>

