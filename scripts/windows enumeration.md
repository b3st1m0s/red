
```
for i in $(cat hosts); do mkdir ./$i; done

run as root:

for i in $(cat hosts); do   
sudo nmap -Pn -vv -n -sS -sVC -p- -T5 --min-rate=5000 --stats-every 10s -oN ./$i/fullscan.txt $i & enum4linux-ng -A $i -oJ ./$i/smbenum & done
```