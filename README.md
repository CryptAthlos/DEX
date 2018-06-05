# DEX

The Exchange Smart-Contract has 3 functions:

1. Funding: It's possible to deposit and withdraw both tokens of any kind and Ether

2. Trading: You can trade any kind of token against ether. Both market orders and limit orders. It's also possible to cancel an order.

3. Manangement: It's possible to add new tokens on the fly.

The Exchange is unit tested with Truffle's Test-Framework.


<h2>Follow the build [instructions](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum) for your respective platform to get geth installed</h2>

Setup and activate a [virtualenv](https://www.linkedin.com/pulse/setup-python-virtualenv-ubuntu-1604-jonathan-froiland/)

```
$ mkdir venv
$ cd venv
$ virtualenv -p python3 dex
$ source dex/bin/activate
```

Clone repository

```
$ git clone https://github.com/CryptAthlos/DEX.git
$ cd DEX
```
In order to work with the smart contracts you need:

1. Node Package Manager
    1. This setup runs 6.1.0

2. Truffle
    1. This setup runs Truffle v4.1.11 (core: 4.1.11)
    2. Solidity v0.4.24 (solc-js)

3. Nodejs
    1. v9.11.1
    
4. Ethereumjs-TestRPC

5. Geth

6. MIST

7. MetaMask

8. Chome Browser

<h1>Running the DEX on a Private Node</h1>

1. Open a terminal (you will have a few seperate terminals open)
2. Make a directory for your genesis file 
    1. (i.e., `$ mkdir privatechain/`)
3. Copy the genesis.json file into the privatechain directory.
4. In that directory make a chaindat directory 
    1. `$ mkdir chaindata`
5. Initialize the privatechain
    1. `geth --datadir=~/privatechain/chaindata/ init ~/privatechain/genesis.json`
    2. Last line should let you know if you successfully wrote genesis state
6. Start a private node
    1. `geth --datadir=~/privatechain/chaindata/ --rpc`

7. Open another terminal
8. Run the following:
    1. `geth attach ipc:/home/<user>/privatechain/chaindata/geth.ipc`
    2. start mining (may take a few minutes to get going)
        1. `miner.start()`
    3. Create an [account](https://github.com/ethereum/go-ethereum/wiki/Managing-your-accounts)
        1. `personal.newAccount()`
        2. Remember your password
        3. if it's your fist account it will also be your coinbase account
    4. Unlock your account
        1. `personal.unlockAccount(eth.accounts[0])`
        2. Enter password

9. Open another terminal to the DEX directory
    1. miner should be running for migrate to work
    2. `$ truffle migrate`
    3. `$ npm run dev`

10. With Mist downloaded and installed--run in a seperate terminal 
    1. `$ /opt/Mist/./mist --rpc ~/privatechain/chaindata/geth.ipc`
    2. Mist should eventually open and connect to the private network
