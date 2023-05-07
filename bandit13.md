# Level 13: 
```sh
mkdir /tmp/testdir && xxd -r data.txt > /tmp/testdir/testfile
```
```sh
file -i testfile
mv testfile testfile.gz
gzip -d testfile.gz
```
```sh
file -i testfile
bzip2 -d testfile
```
```sh
file -i testfile.out
mv testfile.out testfile.gz
gzip -d testfile.gz
```
```sh
file -i testfile
tar -xf testfile
```
```sh
file -i data5.bin
tar -xf data5.bin
```
```sh
file -i data6.bin
bzip2 -xf data6.bin
```
```sh
file -i data6.bin.out
tar -xf data6.bin.out
```
```sh
file -i data8.bin
mv data8.bin data8.gz
gzip -d data8.gz
```
```sh
cat data8
```
#### Password
*`wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw`*
