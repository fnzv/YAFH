## Yet Another Fake Honeypot

### Quickstart

1) Clone repo locally<br>
```git clone https://github.com/fnzv/YAFH.git && cd YAFH``` 
2) Get deps<br>
 ```go get github.com/gliderlabs/ssh && go get github.com/kr/pty```
3) Build and create Go binaries <br>
```go build sshd.go && go build telnetd.go && go build fake-shell.go```
4) Execute the Honeypot(s): <br>
```./sshd``` <br>
```./telnetd``` <br>

<br><br>
- All users trying to connecting via TELNET to port 23 will be shown a fake CISCO router login (Any input will lead to telnet shell) <br>
- All users trying to connect via SSH to port 2222 will login into a fake shell (Password is: password.. it's possible to also remove pass auth &/or use key auth)<br>
- All the actions executed by malicious users will be saved into yafh-telnet.log / yafh-ssh.log, (same dir where you started the binary file) <br><br>
 <br>
If you want it to run 24/7, you can setup a systemd unit/supervisord running in background keeping the script up or just lunch the command with screen <br>



### Running sshd on Docker

1) Inside repo's directory: <br>
```docker build -t fnzv/yafh-sshd -f Dockerfile.ssh .``` 
2) Run the container and Expose the SSH Honeypot on port 22:<br>
```docker run -p 22:2222 -d fnzv/yafh-sshd``` <br>

### Running telnetd on Docker

1) Inside repo's directory: <br>
```docker build -t fnzv/yafh-telnetd -f Dockerfile.telnet .``` 
2) Run the container and Expose the TELNET Honeypot on port 23:<br>
```docker run -p 23:23 -d fnzv/yafh-telnetd``` <br>


### Demo 
[![asciicast](https://asciinema.org/a/7zu9Fzxeg1twjZfnQ7cQilCBq.png)](https://asciinema.org/a/7zu9Fzxeg1twjZfnQ7cQilCBq)

Tested on Ubuntu 16.04
<br>

