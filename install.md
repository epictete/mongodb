# Install MongoDB

### Install _gnupg_ and its required libraries using the following command:

```
sudo apt-get install gnupg
```

### Import the public key used by the package management system:

```
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
```

### Create a list file for MongoDB:

```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```

### Reload local package database:

```
sudo apt-get update
```

### Install the latest stable version of MongoDB packages:

```
sudo apt-get install -y mongodb-org
```
