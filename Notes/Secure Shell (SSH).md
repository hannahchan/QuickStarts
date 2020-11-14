# Secure Shell (SSH)

Secure Shell (SSH) is a cryptographic network protocol for secure remote login from one computer to another. To login to a remote computer from most Linux-based systems, use the command;

    ssh username@hostname

If the SSH client is unavailable, try installing the `openssh-client` package using your Linux distribution's package manager. Install the `openssh-server` package to install a SSH server.

## SSH Keys

One of the key features of SSH is its ability to use public and private keys to authenticate users. You would do this to avoid sending your password over the network. To generate a new SSH key pair interactively, use the command;

    ssh-keygen

The result of running the `ssh-keygen` command is two files, a private key and a public key. They should both have the same name however the public key file will end in `.pub`. Remember to keep your private keys safe.

## Installing a Public Key on a Remote Server

Before you can use your SSH keys to log onto a remote server, you need to install your public key onto the remote server. You can do this by using the following command;

    ssh-copy-id -i PublicKeyFile.pub username@hostname

This command essentially copies your public key to the remote server and stores in a file called `authorized_keys` located in `~/.ssh`.

## Using a Private Key to log into a Remote Server

To use your private key file to log into a remote server, add the `-i` parameter to the ssh command and specify the path to your private key. For example;

    ssh -i PrivateKeyFile username@hostname

If you've added a passphrase to your private key file, you'll have to enter this in for every new SSH session you start with this private key.

## Using the SSH Agent

To minimise the number of times you need to enter in your passphrase, you can use `ssh-agent`. `ssh-agent` caches your private keys and makes them available across multiple SSH sessions in your local login session. Assuming `ssh-agent` is already running, load your private keys by using the following command;

    ssh-add PrivateKeyFile

At this point if your private key requires it, you'll be prompted for your passphrase. From then on you won't be prompted for your passphrase every time you use your private key for the duration of your local login session. When you start a new local login session however, you'll need to reload your private keys.

If `ssh-agent` is not running, you can start it by running;

    eval $(ssh-agent)

Be careful if you put this command in your user profile.

## Agent Forwarding

If you need to connect to a remote server from another remote server in a double-hop situation using SSH, you may want to consider using agent forwarding. Agent forwarding makes available your local `ssh-agent` and the private keys it holds to a remote server for use in authentication. To use agent forwarding, simply add the `-A` parameter to your ssh command;

    ssh -A username@hostname

Only forward your `ssh-agent` to computers you trust! Agent forwarding is used to avoid sending your password over the network and to avoid installing your private keys on multiple hosts.

## The SSH Config File

The SSH config file (`~/.ssh/config`) is a text file you can use to create shortcuts to your most often used SSH commands. For example if you find yourself often using the command `ssh -A -i ~/.ssh/privatekey myname@example.com`, your config file could contain an entry like this;

    Host example
      Hostname example.com
      ForwardAgent yes
      IdentityFile ~/.ssh/privatekey
      User myname

You could then use the command `ssh example` to connect to your remote server with all the settings you specified in the configuration file. The SSH config file is often used to help people remember all the settings they used for their various SSH connections.

## Proxy Jumping

Sometimes the remote server you want to log into is behind one or more proxy hosts. You can use the `-J` option to specify all the proxy hosts that you need to pass through separated by a comma.

    ssh -J proxy1,proxy2,... destination

## References

1. SSH Protocol

   - <https://www.ssh.com/ssh/protocol>

2. ssh-copy-id

   - <https://www.ssh.com/ssh/copy-id>

3. ssh-agent

   - <https://www.ssh.com/ssh/agent>

4. Using an ssh-agent, or how to type your ssh password once, safely

   - <http://rabexc.org/posts/using-ssh-agent>

5. The pitfalls of using ssh-agent, or how to use an agent safely

   - <http://rabexc.org/posts/pitfalls-of-ssh-agents>

6. Simplify Your Life With an SSH Config File

   - <http://nerderati.com/2011/03/17/simplify-your-life-with-an-ssh-config-file>

7. How To Configure Custom Connection Options for your SSH Client

    - <https://www.digitalocean.com/community/tutorials/how-to-configure-custom-connection-options-for-your-ssh-client>

8. SSH to remote hosts though a proxy or bastion with ProxyJump

    - <https://www.redhat.com/sysadmin/ssh-proxy-bastion-proxyjump>
