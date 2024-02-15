# TT-Miner - Version 2024.1.1

## GPU-Miner for Nvidia - Windows & Linux (Hive custom miner package available)
- Ethash, ProgPow, KawPow, Ghostrider, Sha256d, Sha512256d, Sha256dt, Sha3Solidity, Blake3, Sha3D, EthashB3
- Pool & Solo mining (to QT-Wallet & EPIC Listener, Zano-Wallet)
- DAG management, save to disk, mem and swap on GPU
- alternating mining Zil/EPIC/any 2nd or 3rd coin
- Overclocking (core and memory clock lock/offset and power limit)
- separat OC-settings per algo/device
- BTC/BCH lottery (mine solo BCH/BTC with very low hashrate)
- support Intel integrated iGPI (Windows & low memory algos: Sha256d, Sha512256d, Sha256dt, Blake3, Sha3D)


## Mining fees
| Mining | fee |
| - | - |
| Epic Cash | 2.0 % |
| Ghostrider | 2.0 % |
| Solo to Qt-Wallet | 2.0 % |
| BTC/BCH lottery | 1.0 % |
| all other | 1.0 % |


## Supported algos in detail
| Algorithm | remarks |
| - | - |
| Ethash | includes Etchash(Ethereum Classic) & Ubqhash(Ubiq) |
| EthashB3 ||
| KawPow | includes FiroPow(Firo), FiroPoWScc(SCC) |
| ProgPow | includes ProgPowZ(Zano/Chinet/Evolution), EvrProgPow(Evrmore), vProgPow(VeriBlock) and ProgPow(Veil) |
| Ghostrider | includes Mike |
| SHA256D ||
| SHA512256D ||
| SHA256DT ||
| SHA3SOLIDITY | Sha3 Solidity for Etica and BNbitcoin |
| SHA3D ||
| Blake3 ||


## Supported coins in detail
| Algorithm | Coin |
| - | - |
| Ethash | AKA, ZIL, BLACK, EGEM, GRAMS, ETHO, ALT, AVS, OCTA, CLO, EXP, ETP, ETHW, ETHF, REDE, ELH, EGAZ |
| Etchash | ETC |
| EthashB3 | RTH |
| Ubqhash | UBQ |
| ProgPow | EPIC, SERO, VEIL |
| ProgPowZ | ZANO, EVOX |
| vProgPow | VBK |
| EvrProgPow| EVR |
| KawPow | RVN, NEOX, ARL, KAW,PRCO, SATO, HVQ, TTM, ZELS, MEWC, VTE, LAB, CLORE, PAPRY, SATOX, XNA, FRENS |
| FiroPow | FIRO, SCC |
| Ghostrider | RTM, BTRM, BUT, YERB, JGC, NAPI, FITA, BBC, THOON, GSPC, LTR; |
| Mike | VKAX |
| SHA512256D | RXD |
| SHA256DT | NOVO |
| SHA256 | BTC, BCH |
| SHA3D | KCN |
| SHA3SOLIDITY | ETI, BNBTC |
| Blake3 | ALPH |



# Commandline Options
## Simple commandline
To start mining TT needs 2 information:
- What do you want to mine. Option -c (defines the coin you want to mine)
- Where do you want to mine. Option -P (defines the pool you want to use with all information rtequirted: walletid, workername, server and port)

Since you can mine several coins alternating you need may have several different -c and -P on your commandline. To tell TT which belong togeter you should
append an patter of your choice to the command. For Example -cCoin1 and -Pcoin1 or -cEPIC and -PEPIC. Just use the sdame pattern for options that belong together.
If you want to use just a single coin you do not need that and can go with -c and -P.

To start mining ETC you would use this commandline:
#### TT-Miner -cETC ETC -PETC \<ETC-wallet\>.\<ETC-worker\>:\<ETC-password\>@\<ETC-server\>:\<ETC-port\>

If you want to add a backup-pool you can repeat the -PETC option as often as you like. TT will use them as backup-pools in the order you append them.


For epic it will look like this:
#### TT-Miner -cEP EPIC -PEP \<EPIC-wallet\>.\<EPIC-worker\>:\<EPIC-password\>@\<EPIC-server\>:\<EPIC-port\>

To mine EPIC and ETC you just merge the two commandlines:
#### TT-Miner -cEP EPIC -PEP \<EPIC-wallet\>.\<EPIC-worker\>:\<EPIC-password\>@\<EPIC-server\>:\<EPIC-port\> -cETC ETC -PETC \<ETC-wallet\>.\<ETC-worker\>:\<ETC-password\>@\<ETC-server\>:\<ETC-port\>

## Adding ZIL to your existing commandline
If you already mining a coin you can easily add ZIL to your mining. Zil uses alternate mining meaning that TT is mining either you regular coin - or ZIL.
ZIL is active just about 2 minutes per hour. In this time TT mines ZIL for you and switches back to your other coin if the ZIL timesframe passed.
Adding ZIL is as easy as adding any other coin - just append this to your existing command line:
#### -cZ ZIL -PZ \<ZIL-wallet\>.\<ZIL-worker\>:\<ZIL-password\>@\<ZIL-server\>:\<ZIL-port\>
Or - if you weant to mine just ZIL:
#### TT-Miner -cZ ZIL -PZ \<ZIL-wallet\>.\<ZIL-worker\>:\<ZIL-password\>@\<ZIL-server\>:\<ZIL-port\>


## Adding oc options for one of the coins:
Assume you want to mine EPIC and RXD and want to add a mem-lock for RXD at 810 MHz.
First you create your commandline for EPIC & RXD:
#### TT-Miner -cEP EPIC -PEP \<EPIC-wallet\>.\<EPIC-worker\>:\<EPIC-password\>@\<EPIC-server\>:\<EPIC-port\> -cRXD RXD -PRXD \<RXD-wallet\>.\<RXD-worker\>:\<RXD-password\>@\<RXD-server\>:\<RXD-port\>


Then you tell TT to use a memory lock for RXD @ 810 MHz. The commandline option for memory lock is:<br/>
-oc-mem<br/>
To tell TT for which coin you want to apply this you need to append your parrter:<br/>
-oc-memRXD 810<br/>

#### TT-Miner -cEP EPIC -PEP \<EPIC-wallet\>.\<EPIC-worker\>:\<EPIC-password\>@\<EPIC-server\>:\<EPIC-port\> -cRXD RXD -PRXD \<RXD-wallet\>.\<RXD-worker\>:\<RXD-password\>@\<RXD-server\>:\<RXD-port\> -oc-memRXD 810

That's it.


## OC option
TT understand clock-locks and clock-offsets as well as power-limits:
- -oc-core[...] INT = core clock lock
- -oc-coreoff[...] INT = core clock offset
- -oc-mem[...] INT = memory clock lock
- -oc-memoff[...] INT = memory clock offset
- -oc-pl[...][W] INT = power limit. If you specify just a single number TT treats it as percent, If use append a 'W' it uses you setting as absolute Watt limit
- -oc-fan[...] INT = control the fan




## Algo vs. Coin
To define what you want to mine you can use either the algo commandline otpion (-a) or the coin commandline option (-c). There is no need to define both, but there are some points to take care for.
In general it is easier to define which coin you want to mine - that way you do not need to find out which algo fir that coin is required. TT will select the correct algo using the required variant.
Lets say you want to mine Veil, you can either define -c VEIL or you define -a ProgPoWVeil. Since Veil uses a special version of ProgPow you cannot use -a ProgPow - that would lead to rejected shares.
To avoid all these problems it is much easier just to define the coin you want to mine. There are other things to take care of. If you want to mine EPIC (which uses the native ProgPow algo) you can
define -a ProgPow or -c EPIC. But EPIC uses also a special protocol for the communication between miner and pool/server. If you just define -a ProgPow TT cannot know that you want to mine EPIC and
will therefore load the default protocol, but that is not compatibvle with the EPIC protocol. To tell TT that you want the Epic protocol you need to add the protocol information to your -P commandline
option. Sample:<br/>
TT-Miner.exe -a ProgPow -P epic://\<EPIC-USER\>@epicmine.io:3333 - or in the case of a SSL encryptoed communication<br/>
TT-Miner.exe -a ProgPow -P epic+ssl://\<EPIC-USER\>@epicmine.io:3333<br/>

But you can use the easy for with the coin commandline option:<br/>
TT-Miner.exe -c EPIC -P ssl://\<EPIC-USER\>@epicmine.io:3333<br/>

The same issue with ZIL. Zil uses either a stratum version (crazypool.org) or zmp (shardpool.io)
TT-Miner.exe -a Ethash -P zmp://\<ZIL-WALLET\>@eu1-zil.shardpool.io:3333 - or in the case of a SSL encryptoed communication<br/>
TT-Miner.exe -a Ethash -P zmp+ssl://\<ZIL-WALLET\>@eu1-zil.shardpool.io:5555 - or in the case of a SSL encryptoed communication<br/>

Easy for with the coin commandline option:<br/>
TT-Miner.exe -c ZIL -P ssl://\<ZIL-WALLET\>@eu1-zil.shardpool.io:5555<br/>



## Selectors
Since TT allows you to mine alternating coin it is neccessary to combine some options together so that TT can see which options belong together.
If you want to mine EPIC and RXD you may want to set different overclock settings for each algo. To allow this TT introduce 'selectors' for the
command line to combine options for t single algo/coin. Here is a smaple. Lets say you want to mine Epic and RXD. TT needs 2 option to for each coin.
The -c to define the coin and -P for wallet and poolserver:<br/>

TT-Miner.exe -c EPIC -P \<EPIC-USER\>@\<EPIC-SERVER\> - using epicmine.io as a sample<br/>
TT-Miner.exe -c EPIC -P \<EPIC-USER\>@epicmine.io:3333 - if you want to use the SSL encrypted port 3334 please change the line to this:<br/>
TT-Miner.exe -c EPIC -P ssl://\<EPIC-USER\>@epicmine.io:3334<br/>

Now we add Radiant(RXD) as a second coin to this command:<br/>
TT-Miner.exe -c EPIC -P \<EPIC-USER\>@epicmine.io:3333 -c RXD -P \<RXD-WALLET\>@\<RXD-SERVER\><br/>
Unfortunatly TT can not knmow which -P command belongs to EPIC and which one to RXD. For clarify this TT uses \'selectors\'. You just append a pattern you like to the command that belongs together.
Lets use \'Epic\' for EPIC and \'Radiant\' for RXD. This is the resulting command line that uses the choosen selectors:<br/>
TT-Miner.exe -cEpic EPIC -PEpic \<EPIC-USER\>@epicmine.io:3333 -cRadiant RXD -PRadiant \<RXD-WALLET\>@\<RXD-SERVER\><br/>
Use the SSL server of vipor we have this:<br/>

TT-Miner.exe -cEpic EPIC -PEpic \<EPIC-USER\>@epicmine.io:3333 -cRadiant RXD -PRadiant ssl://\<RXD-WALLET\>@de.vipor.net:5166<br/><br/>
<b>Please note:</b> You can still use the \'empty\' selector if you need just a single coin:<br/>
TT-Miner.exe -c RXD -P ssl://\<RXD-WALLET\>@de.vipor.net:5166<br/>





## General Options
| Option | Information |
| - | - |
| -h [ --help, -? ] | Prints supported options, the commandline format and exits. |
| -v [ --version ] | Prints verision information of TT-Miner and exits. |
| -no-color [ -nocolor ] | Do not use any color in the screen output. |
| -no-ctrlc [ -noctrlc ] | Disables 'Ctrl-C' monitoring. |
| -cdd | Create a crashdump file in the case of an access violation. |
| -bm [ -benchmark ] | Runs TT-Miner in benchmark made. In this mode some of the variable settings of an algo are constant so that you can make performance adjustments. This can be usefule for alternating algos like ProgPow, KawPos, Ghostrider and Mike. No shares are sent to the pool or server! |



### Information options
| Option | Information |
| - | - |
| -luck | Prints some information how your mining performs. Does this sessions find shares as expected, more or less |
| -daginfo | Prints information of the active DAG in the mining statistics |
| -rep-i | Sets the timeframe the statistic is printed<br/>Use: -rep-i 30 prints the statistics all 30 seconds<br/>-rep-i 0 disable statistics printing |
| -rep-s | Sets the number of shares after that the statistic is printed<br/>Use: -rep-s 30 prints the statistics all 30 shares |
| -raao | report active algos only. If you want to see the statistics only for the active algo and drop the information for the inactive |


### Log options
| Option | Information |
| - | - |
| -log | Saves all the output of the miner into a logfile. Default logfile: \<TT-MinerFolder\>/Logs/TT-MinerLog-[\<YYYYMMDD\>].log |
| -logpool | Saves all the communication between pool/server and TT-Miner into a logfile. Default logfile: \<TT-MinerFolder\>/Logs/TT-Pool-[\<Server\>-\<Port\>[\<YYYYMMDD\>].log |



### DAG options
| Option | Information |
| - | - |
| -dag-2mem | Keeps a copy of the created DAG in the host memory.<br/><dl><dt>Advantage:</dt><dd>Can reuse the DAG if required (EPIC-Mining, NICEHASH)</dd><dd>Saves energy since the DAG is created on a single GPU only and then distributed to the other GPUs</dd><dd>You can run the GPU that creates the DAG with different OC settings than the other GPUs</dd><dt>Disadvantage:</dt><dd>Needs host memory to keep the DAG</dd></dl> |
| -dag-2disk | Keeps a copy of the created DAG on the disk.<br/><dl><dt>Advantage:</dt><dd>Can reuse the DAG if required (EPIC-Mining, NICEHASH)</dd><dd>Saves energy since the DAG is created on a single GPU only and then distributed to the other GPUs</dd><dd>You can run the GPU that creates the DAG with different OC settings than the other GPUs</dd><dd>Faster start of mining</dd><dt>Disadvantage:</dt><dd>Needs diskspace to keep the DAG</dd></dl> |
| -dag-path | Sets a custom folder to load/save the dag files<br/>Use: -dag-path \<New-Path-To-Dag-Files\> |
| -dag-swap | Allows TT to replace DAGs from Gpu. This allows you to mine coins whose DAGs needs more memory than your GPU have available.<br/>Sample: You want to mine Zil, EPIC and ETC on a 1050Ti offering 4GB available memory. The Dag-size of ETC is already 3.2 GB (as of today) Epic and Zil both needs a DAG with sizes > 1GB. So in total you need more than 5GB and would not be able to mine all three coins. -dag-swap will replace the DAG on the Gpu and you can mine all three coins. |



### CUDA options
| Option | Information |
| - | - |
| -cuda-compute | Sets the compute version for each Gpu<br/>Use: -cuda-compute 61 60 - sets the compute version of the first Gpu in your system to 6.1 and the version of the second Gpu to 6.0. Setting a value of 0 sets the Gpus default |
| -cuda-ver | Sets the cudas version you want to use. This values must be less than the best possible<br/>Use: -cuda-ver 11.4 - TT uses cuda version 11.4 |
| -cuda-grid | Set the grid count TT should use for the algo |
| -cuda-block | Set the block count TT should use for the algo. This value must be a multiple of 32 - better 128. TT will use grid-count * block-count threads for each call of the kernel |


### Temperature control
| Option | Information |
| - | - |
| -tstop | suspends a Gpu if its temperatur exceedes this value |
| -tstart | resumes mining |




# Other samples
### Mine ETC on 2miners (TCP-port) (-o,-u format)
| protocol | commandline |
| - | - |
| TCP port, -P format | TT-Miner -c ETC -P \<WALLET\>.\<WORKER\>@etc.2miners.com:1010 |
| TCP port, -o,-u format | TT-Miner -c ETC -u \<WALLET\>.\<WORKER\> -o etc.2miners.com:1010 |
| SSL port, -P format | TT-Miner -c ETC -P stratum+ssl://\<WALLET\>.\<WORKER\>@etc.2miners.com:11010 |
| SSL port, -o,-u format | TT-Miner -c ETC -u \<WALLET\>.\<WORKER\> -o stratum+ssl://etc.2miners.com:11010 |


## Mine RXD on woolypooly (SSL-port) (-P format)
#### TT-Miner -c RXD -P ssl://\<WALLET\>.\<WORKER\>@pool.woolypooly.com:3122 



# Mining to NiceHash
### Mine Ethash on NiceHash
TT-Miner offers special handling for mining an algo/pool that frequently changes the required DAG. It is recommended to use the 'dag-2file' commandline option. It will save a DAG - once created - to disk. This will save some time the next time the DAG is required. Please see below one possible commandline to mine ETHASH on NiceHash:<br>
#### TT-Miner -dag-2disk -daginfo -a ETHASH -P ssl://\<WALLET\>.\<WORKER\>@daggerhashimoto.auto.nicehash.com:443

### Mine Ethash on NiceHash
#### TT-Miner -dag-2disk -daginfo -a ETCHASH -P stratum+ssl://\<WALLET\>.\<WORKER\>@etchash.auto.nicehash.com:443

### Mine KawPow on NiceHash
#### TT-Miner -dag-2disk -daginfo -a KAWPOW -P stratum+ssl://\<WALLET\>.\<WORKER\>@kawpow.auto.nicehash.com:443




# Mining Solo to a Qt-Wallet
To use your Qt-Wallet for solo mining you need to create/configure a config file. The config file is a textfile that must contain following information:
You need \<USERNAME\> and \<PASSWORD\> in the commandline of TT-Miner to get access to the Qt-Wallet.
Please change rpcallowip to match your network configuration. It defines IPs that may connect to the wallet.<br/>

rem -- FILE START -- do not add this line to your config file!<br/>
automintoff=1<br/>
rpcuser=\<USERNAME\><br/>
rpcpassword=\<PASSWORD\><br/>
rpcbind=0.0.0.0<br/>
rpcallowip=192.168.41.0/24<br/>
server=1<br/>
listen=1<br/>
gen=1<br/>
miningaddress=\<WALLET\><br/>
rem -- FILE END -- do not add this line to your config file!<br/>


## Then start your Qt-Wallet with the option to use this new configuration file:<br/>
neoxa-qt -conf=filename.conf<br/>


## Mine NEOX Solo to Qt-Wallet
Please use the USERNAME and PASSWORD information from your config file that you use to start your wallet.<br/>
#### TT-Miner -c NEOX -P http://\<USERNAME\>:\<PASSWORD\>@\<IP-TO-YOUR-QT-WALLET\>:9766




## Not supported Solo to Qt-Wallet
Some project modified the format of the RPC protocol so that TT is not able to establish a connection to the wallet for solo mining. Please find below a list of known project that do not work:
- Arielcoin(ARL)
- Titanium(TTM)

If you see any addition project that modified the RPC protocol so that solo mining is not supported please let me know.




# Mining EPIC
You have the choice to mine EPIC either directly to the local node, or to one of the EPIC mining pools. Since EPIC is alternating the active algo you can mine something else. If you do not specify a second coin the mining process is paused.


## Sample command lines to mine just EPIC to a local node
#### TT-Miner -c EPIC -P <SOME_ID>.<SOME_WORKER>@127.0.0.1:3416

## Sample command lines to mine just EPIC on fastepic.eu
#### TT-Miner -c EPIC -P ssl://keybaseid_<YOUR_KEYBASE_ID\>.\<YOUR_WORKER_NAME\>:\<YOUR_PASSWORD\>@fastepic.eu:3416

## Sample command lines to mine just EPIC on epicmine.io
#### TT-Miner -c EPIC -P ssl:\<YOUR_ID\>.\<YOUR_WORKER_NAME\>:\<YOUR_PASSWORD\>@de.epicmine.io:3334

## Sample command lines to mine just EPIC on 51pool.online
#### TT-Miner -c EPIC -P \<YOUR_ID\>#\<YOUR_WORKER_NAME\>:\<YOUR_PASSWORD\>@51pool.online:4416


# Joining the BTC/BCH lottery:
To use your personal luck you can join the BTC/BCH lottery. It will mine SOLO BTC or BCH with a very low hashrate.
You will hardly notice the impact on your system. Just append this to your existing commandline:<br/>
#### -lottery BCH <YOUR-BCH-WALLET> for BitcoinCash or
#### -lottery BTC <YOUR-BTC-WALLET> for Bitcoin

You can also just use TT for the lottery:
#### TT-Miner -lottery BCH <YOUR-BCH-WALLET>


------------------------------------
## known issues/bugs
There is a bug on some system mining at rplant. I'm working on this. If someone have crashes/freezes with rplant please get in touch with me.

------------------------------------
If you have any issues to setup your commandline please do not hesitate to contact me or join the TT-Miner discord server. I'm happy to help if I can.
