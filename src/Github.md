Github SSH
==========

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa): /home/user/.ssh/github-id_rsa
Created directory '/home/user/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/user/.ssh/github-id_rsa.
Your public key has been saved in /home/user/.ssh/github-id_rsa.pub.
The key fingerprint is:
SHA256:rgxu3euR+eT0ewxuALfZw8T6vxWsMHaMEDct3M+P+p0 your_email@example.com
The key's randomart image is:
+---[RSA 4096]----+
|         ..oo    |
|          oo.o   |
|         . .. o  |
|        . o = .o |
|        So % o +.|
|       . o* O o o|
|    .. .= o+ *  .|
|   ..o...* .= oo.|
|   .. o.o.o.o=+E.|
+----[SHA256]-----+

# Adding your SSH key to the ssh-agent
$ eval "$(ssh-agent -s)"
Agent pid 9721

# Add your SSH private key to the ssh-agent
$ ssh-add ~/.ssh/github-id_rsa
Identity added: /home/user/.ssh/github-id_rsa (/home/user/.ssh/github-id_rsa)

# Copy the SSH key and add it to your github account
$ cat .ssh/github-id_rsa.pub

# Testing your SSH connection
$ ssh -T git@github.com
```
