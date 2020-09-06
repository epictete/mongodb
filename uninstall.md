# Uninstall MongoDB

### Stop MongoDB:

```
sudo service mongod stop
```

### Remove Packages:

```
sudo apt-get purge mongodb-org*
```

### Remove Data Directories:

```
sudo rm -r /var/log/mongodb

```

```
sudo rm -r /var/lib/mongodb
```
