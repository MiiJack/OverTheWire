# Level 23:
Like in the previous level :
```sh
cd /etc/cron.d
cat cronjob_bandit23
```
And:
```sh
cat /usr/bin/cronjob_bandit23.sh
```
We can see:
```sh
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```
In order to solve the level, we will have to execute the script as bandit23 (let's replace whoami with bandit23). 

```sh
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
```
This returns ``8ca319486bfbbc3663ea0fbe81326349``.
```sh
cat /etc/bandit_pass/bandit23 > /tmp/8ca319486bfbbc3663ea0fbe81326349
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```
#### Password
*`QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G`*
