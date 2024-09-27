# Uninvited-Guest
Uninvited Guest - A file server for files over DNS TXT records

First set up your domain to point to which ever server you're hosting this on.

Then run the python server

```./server --domain domainname.com --directory /dir/of/tools```

It will only support a flat directory structure in /dir/of/tools

You will need to write your own client to receive files. The count of items will be in file.count.domainname.com and the strings will be in file.number.domainname.com.

An example bash client would be something like:

```f="pwned.png";d="6-9.eu";c=$(dig +short txt $f.count.$d|tr -d \");for i in $(seq 0 $c);do echo -n $(dig +short txt $f.$i.$d|tr -d \");done | base64 -d > /tmp/pwned.png```
