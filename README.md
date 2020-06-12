
# GitLab-Setup
To Setup internal GitLab Server
## Modify /etc/hosts
For **GNU/Linux** and **macOS** User
```sh
$ vi /etc/hosts
```
Add Below line to your hosts file and save it
```
10.109.190.251 iluvgit.fstop.com.tw
```
 <br><br>


For **Windows** User
```sh
$ edit c:\Windows\System32\Drivers\etc\hosts
```
Add Below line to your hosts file and save it
```
10.109.190.251 iluvgit.fstop.com.tw
```

---
## Login to GitLab
[FSTOP GitLab](https://iluvgit.fstop.com.tw/)

Fill `Username` and `Password`, Click `Sign in` Button


<img src="/assets/images/signin.png" width="500">

| :warning:  If you cannot login with your default password, or don't have an account please mail to [KFC](mailto:kfchang@fstop.com.tw) |
| --- |



---

## Access GitLab via your endpoint
### Create SSH Key
To support SSH, GitLab requires the installation of the OpenSSH client, which comes pre-installed on GNU/Linux and macOS, but not on Windows.


Navigate to your terminal, check ssh version
```
$ ssh -V

OpenSSH_7.7p1, LibreSSL 2.7.3
```


Generate SSH keys for gitlab
For `Enter passphrase (empty for no passphrase):` and 
`Enter same passphrase again:` just press `enter key`
```
$ ssh-keygen -o -f ~/.ssh/id_rsa_iluvgit

Password:
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/Kai-FengChang/.ssh/id_rsa_iluvgit.
Your public key has been saved in /Users/Kai-FengChang/.ssh/id_rsa_iluvgit.pub.
The key fingerprint is:
SHA256:V54kwASwLQbGdSA2IcpEak761DiHkuT33+0brobo64k root@Kai-FengdeMacBook-Pro.local
The key's randomart image is:
+---[RSA 2048]----+
|o+Bo+oo+o        |
|=+.+ +  ..       |
|o=  + .   . o    |
|B. = .     = .   |
|+o=.o   S . o    |
| +.o.    .       |
|  .  .. .  .     |
|    ..o...o .    |
|   Eo=...oo=.    |
+----[SHA256]-----+
```

Copy SSH Keys
```
$ cat ~/.ssh/id_rsa_iluvgit.pub

ssh-rsa Thisislllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllllloooooooooooooooooooooooooooooooooooooooooooooooonnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnngggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggkey root@Kai-FengdeMacBook-Pro.local
```

### Copy Keys to GitLab
Navigate to [FSTOP GitLab](https://iluvgit.fstop.com.tw/) and login

Click at Avatar at top-right corner, <br>
At drop-down menu, click `Settings` 


<img src="/assets/images/settings.png">
<br>

At left Side Panel, click `SSH Keys`

<img src="/assets/images/sshkeys.png" height="450">
<br>

Paste the `SSH Key` you just copied, filled the `title` and `expired at`
then click `Add key` button

<img src="/assets/images/sshkeys-content.png">
<br>

Once you created, it should appear the page shown as follows


<img src="/assets/images/sshkey-content-done.png">
<br>

## Verify Connection

Type below command to verify connection
```
$ ssh -T git@iluvgit.fstop.com.tw
Welcome to GitLab, @KFC!
```

If it appears `Welcome to GitLab, @XXX!`<br>
Congratulations, you do the job best!!
