# Building on Ubuntu 16.04 LTS
1. Run Ubuntu terminal (Search your computer -> Terminal)

2. Install all required packages
```
sudo apt-get update
sudo apt-get install git cmake openssl libssl-dev autoconf automake libtool libcurl4-openssl-dev libboost-all-dev build-essential
```

3. Select or create a directory for Gravity source code. In this example we use the home directory
```
cd ~
```

4. Clone the source code repository. After the first command you will be requested for your login and password in Unfuddle
```
git clone https://github.com/GravityProtocol/gravity-core
cd gravity-core
git submodule update --init --recursive
```

5. Run the command to prepare the package to use libtool
```
libtoolize
```

6. Delete cmake cache file and build folder
```
rm -f CMakeCache.txt
rm -f -r build
```

7. Run cmake with path to ssl libraries
```
cmake -DOPENSSL_ROOT_DIR=/usr/lib/ssl/openssl -DOPENSSL_LIBRARIES=/usr/lib/ssl
```

After successful execution you will see the following
```
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/user/src/gravity/gravity-core
```

8. Start the compilation. It can take 20 minutes or more depending on the hardware
```
make
```
