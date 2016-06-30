

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


## Build samples ( and genomic-storage as well )
```
cd build.release
CASABLANCA_DIR=/home/abokov/github/abokov/casablanca CXX=g++-4.8 cmake .. -DCMAKE_BUILD_TYPE=Release -DBUILD_SAMPLES=ON
make
```

## Run GenomicStorage

### Getting account name and key

You need to login into Azure portal, goto Storage Account blade and create new (or use existing storage account ) - as soon as it created you need to get account name and key ( you can you primary key as well as secondary ). Note keys and account name from example are used as example and shouldn't be used in real life ( almost because this storage account is non exists :-))

![Azure portal](/img/storage_credentials.png)


## Usage of binary 'genomicstorage'
After compile (in case of no errors ) binaries are located in
'azure-storage-cpp/Microsoft.WindowsAzure.Storage/build.release/Binaries', so you can run 
```
./genomicstorage   _name_of_account_   _account_key_    _container_name_    _blob_name_     _upload_file_
```
Inside application there's some simple checking for params as well as catching exceptions, so in case of any error you will will see more-less detailed messages.

##What is inside GenomicStorage class :

Things are pretty simple :
### Init
takes all required params, do validation, but no any actions (like Azure API calls ), so nothing created/deleted/copied on that stage. If failed, returns false.

### Save/Load/Run/other verbs
These guys are doing actions








