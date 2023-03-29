
Ubuntu CA Install
https://ubuntu.com/server/docs/security-trust-store

```
$ sudo apt-get install -y ca-certificates
$ sudo cp local-ca.crt /usr/local/share/ca-certificates
$ sudo update-ca-certificates
```

