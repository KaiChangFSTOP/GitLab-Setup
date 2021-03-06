| :warning:  以下操作，請連入公司VPN！！，若無法連入VPN， 請主管協助開通|
| --- |

| :warning:  請先務必安裝完git-scm，如尚未安裝，請參考[git install](https://git-scm.com/downloads)！！ |
| --- |


# GitLab-Setup
To Setup internal GitLab Server
## Modify /etc/hosts
For **GNU/Linux** and **macOS** User
```sh
$ vi /etc/hosts
```
Add Below line to your hosts file and save it
```
10.109.190.240 flow.fstop.com.tw
```
 <br><br>


For **Windows** User
```sh
$ edit c:\Windows\System32\Drivers\etc\hosts
```
Add Below line to your hosts file and save it
```
10.109.190.240 flow.fstop.com.tw
```

---
## Login to GitLab
[FSTOP Flow](https://flow.fstop.com.tw/)




| :warning:  If you have problem to visit the web page, do follow this [instruction](https://medium.com/@dblazeski/chrome-bypass-net-err-cert-invalid-for-development-daefae43eb12) to fix it |
| --- |


Fill `Username` and `Password`, Click `Sign in` Button

The `Username` is the name in email, `Password` is `P@ssw0rd`. <br>
For example, `kfchang@fstop.com.tw`, `Username` is `kfchang`, `Password` is `P@ssw0rd`


<img src="/assets/images/signin.png" width="500">


The first time when you login, it will ask you to modiy your password

| :warning:  If you cannot login with your default password, or don't have an account please mail to [KFC](mailto:kfchang@fstop.com.tw) |
| --- |





---

## Access GitLab via your endpoint
### Create SSH Key
To support SSH, GitLab requires the installation of the OpenSSH client, which comes pre-installed on GNU/Linux and macOS, but not on Windows.
[reference](https://gitlab.com/help/ssh/README#generating-a-new-ssh-key-pair)

Navigate to your terminal, check ssh version
```
$ ssh -V

OpenSSH_7.7p1, LibreSSL 2.7.3
```


Generate SSH keys for gitlab
For `Enter passphrase (empty for no passphrase):` and 
`Enter same passphrase again:` just press `enter key`
```
$ ssh-keygen -t ed25519 -C "<comment>"

Password:
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/Kai-FengChang/.ssh/id_rsa_ed25519.
Your public key has been saved in /Users/Kai-FengChang/.ssh/id_rsa_gitlab_ed25519.pub.
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

macOS
```
$ pbcopy < ~/.ssh/id_ed25519.pub
```

Git Bash on Windows
```
$ cat ~/.ssh/id_ed25519.pub | clip
```

### Copy Keys to GitLab
Navigate to [FSTOP Flow](https://flow.fstop.com.tw/) and login

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

## Disable SSL verification
at terminal, type following command
```
git config --global http.sslVerify false
```

## Verify Connection

Type below command to verify connection
```
$ ssh -T git@flow.fstop.com.tw
Welcome to GitLab, @KFC!
```

If it appears `Welcome to GitLab, @XXX!`<br>
Congratulations, you do the job best!!


## Verify Project Clone and Push

```
$ git clone git@flow.fstop.com.tw:KFC/demo-project.git
$ cd demo-project
$ echo <your-username> >> <your-username>.md
$ git add .
$ git commit -m"<your-username>"
$ git push
```

example shown as below
```
$ git clone git@flow.fstop.com.tw:KFC/demo-project.git
$ cd demo-project
$ echo KFC >> KFC.md
$ git add .
$ git commit -m"KFC"
$ git push
```
## (OPTIONAL) link sourcetree to your gitlab account

[reference](https://stackoverflow.com/questions/53184950/sourcetree-gives-me-a-login-error-when-i-try-to-add-my-gitlab-account)

謝謝Ian Huang (黃景毅前輩) 提供！


