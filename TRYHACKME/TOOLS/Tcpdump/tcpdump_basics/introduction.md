# TCPDUMP

tcpdump is a command-line network packet analyzer used to caputre and inspect network traffic in real time. Wireshark is an gui based packet analysis whereas tcpdump does terminal based packet capture and analyssi 

- tcpdump uses teh `libcap` library to capture packets

## How to run it 

#### specify the network interface

the first we need to decide is which network interface to listen to using `-i INTERFACE` . we can listen on all available interfaces using `-i any` , alternatively we can specify like this : `-i eth0` 

- first we need the list of avaible network interface 

  ```bash
  ip a s 
  #or 
  ip address show
  ```

- first to listen on a specifc network interface we need to do this : 

  ```bash
  tcpdump -i eth0
  ```

- if we wanna listen all available network interface : 

  ```bash
  tcpdump -i any
  ```

- if we wanna save the captured packets we need to use this : the file extension is most commonly set to the .pcap

  ```bash
  tcpdump -i eth0 -w FILE
  ```

- now if we wanna read the saved packets from a file : 

  ```bash
  tcpdump -r FILE
  ```

- If we wanna limit the no of packets to capture : 

  ```bash
  tcpdump -i eth0 -c COUNT
  ```

- if you dont' wanna resovle the ip address use single -n if you don't wanna resolve the port also use -nn 

  ```bash
  tcpdump -i eth0 -c 5 -nn
  ```

- if you want more verbose output: -v produces some -vv produces some more -vvv produces more and more 

  ```bash
  tcpdump -i eth0 -c 5 -v 
  ```

  