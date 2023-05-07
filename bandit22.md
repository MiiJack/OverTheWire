# Level 22:
```sh
cd /etc/cron.d && ls
```
We will see the following ``cronjob_bandit15_root  cronjob_bandit17_root  cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  cronjob_bandit25_root  e2scrub_all  otw-tmp-dir  sysstat``.
Since we are trying to get to bandit22, let's look inside ``cronjob_bandit22``.
```sh
cat cronjob_bandit22
```
And we get :
```sh
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```
Let's check the content of ``/usr/bin/cronjob_bandit22.sh``
```sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
Trying to execute ``./cronjob_bandit22`` will lead to ``-bash: ./cronjob_bandit22: Permission denied``
By now, we should know our way to deal with permissions.
```sh
mkdir /tmp/bandit22
cd /etc/crond.d 
cp cronjob_bandit22 /tmp/bandit22
cd /tmp/bandit22 && chmod 777 cronjob_bandit22 && ./cronjob_bandit22
```
Now that the cronjob has been successfully executed,
```sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
#### Password
*`WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff`*
