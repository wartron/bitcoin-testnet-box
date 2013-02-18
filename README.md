Testnet-box commands: init, clean, start

    $ testnet-box [command] (N)

    $ testnet-box init (N)

    $ testnet-box clean (N)

    $ testnet-box start (N)


Bitcoin RPC commands

    $ testnet-box (ID) [command]
    
    $ testnet-box getinfo

    $ testnet-box 1 getnewaddress



===

This is a private, difficulty 1 testnet in a box.

Use it as follows:

  $ testnet-box init && testnet-box start

This will start two nodes. You need two because otherwise the node won't
generate blocks. You now have a private testnet:

  $ testnet-box getinfo
  bitcoind -datadir=1  getinfo
  {
    "version" : 60006,
    "protocolversion" : 60000,
    "walletversion" : 60000,
    "balance" : 550.00000000,
    "blocks" : 130,
    "connections" : 1,
    "proxy" : "",
    "difficulty" : 0.12500000,
    "testnet" : true,
    "keypoololdest" : 1335827404,
    "keypoolsize" : 101,
    "paytxfee" : 0.00000000,
    "errors" : ""
  }
  bitcoind -datadir=2  getinfo
  {
    "version" : 60006,
    "protocolversion" : 60000,
    "walletversion" : 60000,
    "balance" : 0.00000000,
    "blocks" : 130,
    "connections" : 1,
    "proxy" : "",
    "difficulty" : 0.12500000,
    "testnet" : true,
    "keypoololdest" : 1335826149,
    "keypoolsize" : 101,
    "paytxfee" : 0.00000000,
    "errors" : ""
  }

To start generating blocks:

  $ testnet-box generate-true
  
To stop generating blocks:

  $ testnet-box generate-false
  
To stop the two nodes:
  
  $ testnet-box stop
  
To clean up any files created while running the testnet 
(and restore to the original state of 130 blocks)

  $ testnet-box clean

Like all testnet nodes, it is listening on port 18333.
