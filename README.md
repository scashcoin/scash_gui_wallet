# Secure Cash GUI wallet

_This is the reference code for lite GUI wallet for the [Secure Cash (SCSX)](http://getsecurecash.org) cryptocurrency._

## Features

- CPU miner for official scash pool
- Remote node sync
- No local blockchain storage
- Send SCSX
- Receive SCSX
- Address book
- CSV export
- Transactions history
- Create wallet
- Open wallet
- Backup wallet
- Import keys
- Export keys
- Encrypt wallet
- Select connecting master node
- Custom remote node connection
- Custom local node connection


## How to compile

### Compile on Ubuntu 16.04 (64 bit)

**1. Install dependencies**

- run an update

``
sudo apt-get update
``

- get all dependencies

``
sudo apt-get install build-essential python-dev gcc g++ git cmake libboost-all-dev librocksdb-dev qt5-default qttools5-dev-tools software-properties-common autotools-dev libicu-dev libbz2-dev zip unzip libsnappy-dev zlib1g-dev libbz2-dev
``

- Remove old boost (if boost version too low)

``
sudo apt-get remove -y libboost-dev libboost-all-dev
``

- Install Boost 1.65.0

``
wget https://dl.bintray.com/boostorg/release/1.65.0/source/boost_1_65_0.tar.bz2
``

``
tar xvjf boost_1_65_0.tar.bz2
``

``
cd boost_1_65_0
``

``
./bootstrap.sh --prefix=/usr/local
``

``
./b2
``

``
sudo ./b2 install
``

- Install Rocksdb

``
git clone https://github.com/facebook/rocksdb.git
``

``
cd rocksdb
``

``
make all
``

**2. Get the source**

``
git clone https://github.com/scashcoin/scash-gui-wallet.git scash-gui-wallet
``

**3. Set permissions**

- navigate to:

``
cd scash-gui-wallet/cryptonote/external/rocksdb/build_tools
``

``
chmod +x build_detect_platform version.sh
``

**4. Prepare the build**

- Navigate back to source folder

``
cd && cd scash-gui-wallet
``

- Prepare the build

``
mkdir build && cd build
``

``
cmake -DSTATIC=ON -DCMAKE_BUILD_TYPE=RELEASE ..
``

**5. Get Rocksdb library**

- Navigate to `lib` folder

``
cd && cd scash-gui-wallet/lib
``

- Unzip the _rocksdb.lib_ library to `build` folder

``
sudo unzip rocksdb.zip -d ~/scash-gui-wallet/build
``

**6. Build**

- Navigate to `build` folder

``
cd && cd scash-gui-wallet/build
``

- Export flags

``
export CXXFLAGS="-std=gnu++11"
``

- Build

``
make
``

_Your executables will be located in `build/src` folder._



### Compile on Windows 7/10 (64 bit)


**1. Install dependencies**

Recommended: Microsoft Visual Studio 14 2015, CMake 3.11.1, Boost 1.65.1 and Qt 5.10.0

Get dependencies:
- http://www.microsoft.com
- [http://www.cmake.org](https://cmake.org/files/v3.11/)
- [http://www.boost.org](https://sourceforge.net/projects/boost/files/boost-binaries/1.65.1/)
- [https://www.qt.io](https://download.qt.io/new_archive/qt/5.10/5.10.0/)

**2. Get sources & libs**

1. Create an account on [GitHub.com](github.com) or log in to an existing one
2. Fork [scash gui wallet](https://github.com/scashcoin/scash-gui-wallet.git) or/and download it

**3. Configure, generate the project files, and Build**

- Fist edit CMakeLists.txt and add boost_1_65_1 and QT 5.10.0 directory.
- Create 'build' directory.
- start CMake GUI and navigate to the repository folder using the field _Where is the source code:_
- Click in configure, mark With_MD_Library, click in generate, after click in open project.
- in Visual Studio 2015, click in rocksdb, project options, go to change Warning on Error: On to OFF.
- Switch solution to `release` instead 'debug'
- Build all project,ready, your Secure Cash GUI Wallet is build in directory 'build/release'.


If you try to build this GUI Wallet with other versions of Visual Studio, QT and Boost, you might come across thousands of bugs and errors that don't make any sense, before finding this I spent days trying to figure out what the hell was going on.

