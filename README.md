

# How to build

## Getting sources

```
mkdir my-project
cd my-project
git clone it@github.com:abokov/azure-storage-cpp.git
git clone git@github.com:abokov/cpprestsdk.git casablanca
```

## Setting up libraries

Required by cpprestsdk (yes you already have git as soon as you did a clone on previous step )
```
sudo apt-get install g++ git make libboost-all-dev libssl-dev cmake
```

Required by  azure-storage-cpp
```
sudo apt-get install libxml++2.6-dev libxml++2.6-doc uuid-dev
```

## Build CPP Rest SDK
```
cd casablanca/Release
mkdir build.debug
cd build.debug
cmake .. -DCMAKE_BUILD_TYPE=Debug
make
```

## Build azure-storage-cpp
```
cd azure-storage-cpp/Microsoft.WIndowsAzure.Storage
mkdir build.release
cd build.release
CASABLANCA_DIR=<path to Casablanca> CXX=g++-4.8 cmake .. -DCMAKE_BUILD_TYPE=Release
make
```

// for example CASABLANCA_DIR=CASABLANCA_DIR=/home/abokov/github/abokov/casablanca










