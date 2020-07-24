# Secure Shell (SSH) Tunnelling #

The Secure Shell (SSH) protocol can be used to create an encrypted network tunnel between a SSH client and SSH server that can be used by other applications to send traffic over. This process is also known as SSH port forwarding and there are three types. All command are executed on the local SSH client.

## Local Port Forwarding ##

Connections to a local SSH client are forwarded via the SSH server and then to a destination server. To use local port forwarding, run the following command;

	ssh -L LocalPort:DestinationServer:DestinationPort Username@SSHServer

Multiple local ports can be forwarded by stringing together multiple `-L` options in the SSH command.

## Remote Port Forwarding ##

Connections to a remote SSH server are forwarded via the SSH client and then to a destination server. This is sometimes referred to as reverse tunnelling. To use remote port forwarding, run the following command;

	ssh -R RemotePort:DestinationServer:DestinationPort Username@SSHServer

Multiple remote ports can be forwarded by stringing together multiple `-R` options in the SSH command.

## Dynamic Port Forwarding ##

Dynamic port forwarding turns a SSH client into a Socket Secure (SOCKS) proxy server. Connections from various applications are forwarded via the SSH client, then via the SSH server and finally to destination servers.

SOCKS is a little-known but widely-implemented protocol for programs to request Internet connections through a proxy server. Each program that uses the proxy server needs to be configured specifically and reconfigured when you stop using the proxy server.

To use dynamic port forwarding and turn your SSH client into a SOCKS proxy server, run the following command;

	ssh -D LocalPort Username@SSHServer

The standard SOCKS port is `1080`. It can be any port however some applications will only work if you use the standard port.

## Other Useful SSH Options ##

When using SSH port forwarding, you may find the following options useful.

| Option | Description                                                                                                                                                |
|:-------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| -C     | Requests compression of all data. Compression is desirable on modem lines and other slow connections, but will only slow down things on fast networks.     |
| -f     | Requests `ssh` to go to background just before command execution.                                                                                          |
| -g     | Allows remote hosts to connect to forwarded ports. Without this option, SSH only listens for connections to the forwarded ports on the loopback interface. |
| -N     | Tells `ssh` not to execute any remote commands. This is useful for just forwarding ports.                                                                  |

## References ##

- SSH tunnel - https://www.ssh.com/ssh/tunneling/
- How to Set up SSH Tunneling (Port Forwarding) - https://linuxize.com/post/how-to-setup-ssh-tunneling/
- ssh(1) - OpenBSD manual pages - https://man.openbsd.org/ssh
- SSH FAQ: TCP port forwarding and the -g (GatewayPorts) option http://www.snailbook.com/faq/gatewayports.auto.html
