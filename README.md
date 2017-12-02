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
 <br>
If you want it to run 24/7, you can setup a systemd unit/supervisord running in background keeping the script up or just lunch the command with screen <br>


### Running on Docker

1) Inside repo's directory: <br>
```docker build -t fnzv/yafh .``` 
2) Run the container:<br>
```docker run -p 23:23 -d fnzv/yafh``` <br>

3) Now the honeypot is running inside a docker container and listening on port 23<br>

### Test 

```
telnet 127.1 23
Trying 127.0.0.1...
Connected to 127.1.
Escape character is '^]'.
This device is for authorized personnel only.
If you have not been provided with permission to
access this device - disconnect at once.
*** Login Required.  Unauthorized use is prohibited ***
*** Ensure that you update the system configuration ***
*** documentation after making system changes.      ***
User Access Verification:
Password:

GW-EXTERNAL >
GW-EXTERNAL >enable
GW-EXTERNAL #
GW-EXTERNAL #ping 8.8.8.8
64 bytes from  8.8.8.8 : icmp_seq = 0  ttl = 20  time= 26.  ms
64 bytes from  8.8.8.8 : icmp_seq = 1  ttl = 40  time= 26.  ms
64 bytes from  8.8.8.8 : icmp_seq = 2  ttl = 30  time= 24.  ms
64 bytes from  8.8.8.8 : icmp_seq = 3  ttl = 0  time= 20.  ms
GW-EXTERNAL #
```


Tested on Ubuntu 16.04
<br>

