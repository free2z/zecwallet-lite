## ZecWallet Lite
Zecwallet Lite is zaddr-first, Sapling-compatible lightwallet client for Zcash. It has full support for all Zcash features:
- Send + receive shielded transactions
- Supports transparent addresses and transactions
- Full support for incoming and outgoing memos
- Fully encrypt your private keys, using viewing keys to sync the blockchain

## WARNING! Experimental
* This is experimental software under active development.
* When we make a release version we will include instructions for download.
* Until that time, please only use if you know specifically what you are doing!!

## Privacy
* While all the keys and transaction detection happens on the client, the server can learn which blocks contain your shielded transactions.
* The server also learns other metadata, including your IP address.
* Finally, note that taddr doesn't provide privacy on-chain.


### Note Management
Zecwallet Lite does automatic note and utxo management, which means it doesn't allow you to manually select which address to send outgoing transactions from. It follows these principles:
* Defaults to sending shielded transactions, even if you're sending to a transparent address
* Sapling funds need at least 5 confirmations before they can be spent
* Can select funds from multiple shielded addresses in the same transaction
* Will automatically shield your transparent funds at the first opportunity
    * When sending an outgoing transaction to a shielded address, Zecwallet-Lite can decide to use the transaction to additionally shield your transparent funds (i.e., send your transparent funds to your own shielded address in the same transaction)

## Compiling from source
Zecwallet Lite is written in Electron/Javascript and can be build from source. It will also automatically compile the Rust SDK needed to run Zecwallet Lite.

#### Pre-Requisites
You need to have the following software installed before you can build Zecwallet Lite

* [Nodejs v12.16.1 or higher](https://nodejs.org)
* [Yarn](https://yarnpkg.com)
* [Rust v1.40+](https://www.rust-lang.org/tools/install)
* [Electron](https://www.electronjs.org/)

```
git clone https://github.com/zingolabs/zecwallet-lite.git
cd zecwallet-lite

yarn install
yarn build
```

The following instructions are tested on Arch Linux:

```
yarn start
```

You should see `Starting the development server...`
and then `Compiled successfully!` printed out in this terminal.

Then, in another terminal instance, run

```
electron .
```

Two windows should open, one for the app and one for debugging.

### Troubleshooting

When running `yarn start` in container:

```
[69610:0604/063542.193055:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /workspaces/free2z/zingolabs/zecwallet-lite/node_modules/electron/dist/chrome-sandbox is owned by root and has mode 4755.
```

This can be solved:

```
sudo chown root:root node_modules/electron/dist/chrome-sandbox
sudo chmod 4755 node_modules/electron/dist/chrome-sandbox
```

> :alert: Zecwallet-Lite is NOT an official wallet
> and is not affiliated with the Electric Coin Company in any way.
