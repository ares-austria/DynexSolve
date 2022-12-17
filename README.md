# DynexSolve
Mining software supporting algo DynexSolve. Currently supporting CUDA

Requirements:
- libcurl (Ubuntu: sudo apt install curl)

# DynexSolve v.2.2.0 Release Notes
* Note: only this version is supported from the network!
* Improved Stratum protocol handling
* Memory overflow fixes
* Improved security

# DynexSolve v.2.1.2 Release Notes
* Note: only this version is supported from the network!
* Improved performance
* Security enhancements
* Stratum/Pool communication improvements

# DynexSolve v.2.1.1 Release Notes
* Much improved net hash-rate on pools
* No more Mallob JSONXX errors
* No more Stratum JSONXX errors
* No more Mallob SSL errors
* automatic re-login to pool upon disconnect, send message failure, etc.
* Supports custom difficulty when pool mining (command option -stratum_dif XXX) - Attention: your pool needs to support custom difficulty
* Connects to our enhanced and optimized Mallob system (the heritage mallob endpoint will be available until end of this week)
* General security enhancements

Pool operators: Custom diff must follow the following login scheme - please make sure you have set the custom diff character accordingly:
ADDRESS.PAYMENTID+DIFF

# Pre-compiled binaries
The official Dynex releases contain pre-compiled binaries of DynexSolve for multiple operating Systems:
https://github.com/dynexcoin/Dynex/releases

# Start mining:

Dynex has developed a proprietary circuit design, the Dynex Neuromorphic Chip, that complements the Dynex ecosystem and turns any modern device into a neuromorphic computing chip that can perform orders of magnitude faster than classical or quantum methodologies for a wide range of applications. Especially due to the dominance of ASICs in the proof-of-work token mining industry, there is a large amount of dormant FPGA infrastructure available which can be converted into high performance next-generation neuromorphic computing clusters. All participating nodes together constitute one enormous neuromorphic computing network. Consequently, the platform is capable of performing computations at unprecedented speeds and efficiency – even exceeding quantum computing.

### Solo mining
To run the Dynex Solve mining software, use the following command:

```
Linux based systems:
./dynexsolve -mining-address <WALLET ADDRESS> -no-cpu -mallob-endpoint https://dynex.dyndns.org/dynexmallob

Windows based systems:
dynexsolvevs -mining-address <WALLET ADDRESS> -no-cpu -mallob-endpoint https://dynex.dyndns.org/dynexmallob
```

Note that the miner output shows computation speed, number of chips which are simulated, etc. Information about mining rewards can be observed in your wallet. When you start the DynexSolve miner, it will by default the GPU with device ID zero (the first installed one). You can specify another GPU if you like by using the command line parameter “-deviceid <ID”. To query the installed and available devices, you can use the command line option “-devices” which will output all available GPUs of your system and the associated IDs. A list of all available commands can be retrieved with the option “-h”.

### Pool mining
Pools are operated by independent pool operators and are there to share mining power and returns. Even if the network difficulty is high, you can still get a share of all blocks mines by a pool. These are usually based on the standard protocol Stratum which is compatible with our DynexSolve miner. Your pool operator can provide you with the right starting configuration / command line options for your environment

When you run DynexSolve for the first time, you will be assigned a unique “Mallob Network ID”. This helps the network to identify and schedule the computational jobs. Mallob is short for “Malleable Load Balancer”, which is a central part of Dynex’ distributed computing management. More information is also avaiable on our website: 
https://dynexcoin.org/get-dnx/#mining

# Build from source
You can build the mining software from source. To do so, clone the repository and make sure you have the following requirements:

* CUDA Environment (cuda development kit, nvcc & latest drivers)
* libcurl 

You need the cryptographic library which is available from building or downloading the main Dynex daemon. For Windows operation systems you require the file "Crypto.lib", on Linux it is "LibCrypto.a". Both files are also added in this repository.

Build command:

```
nvcc ip_sockets.cpp portability_fixes.cpp tcp_sockets.cpp dprintf.cpp jsonxx.cc Dynexchip.cpp kernel.cu -o dynexsolve -O4 -lcurl libCrypto.a
```

## Example: Build for Linux Ubuntu (22.0.4, 20.0.4) with dependencies:

```
sudo apt-get update && sudo apt-get -y upgrade;
sudo apt install -y build-essential git cmake libboost-all-dev libcurl4-openssl-dev nvidia-cuda-toolkit;
mkdir dynexbuild && cd dynexbuild;
git clone https://github.com/dynexcoin/Dynex.git;
cd Dynex && mkdir build && cd build && cmake .. && make;
cd ../../;
git clone https://github.com/dynexcoin/DynexSolve.git;
cd DynexSolve && cp ../Dynex/build/src/libCrypto.a .;
nvcc ip_sockets.cpp portability_fixes.cpp tcp_sockets.cpp dprintf.cpp jsonxx.cc Dynexchip.cpp kernel.cu -o dynexsolve -O4 -lcurl libCrypto.a;
```
