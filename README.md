<div align="center">
<img src="https://github.com/aiken-lang/fortuna/blob/main/assets/logo_white/Fortuna_circle_horizontal.png?raw=true#gh-dark-mode-only" alt="Fortuna" height="200" />
  <img src="https://github.com/aiken-lang/fortuna/blob/main/assets/logo_razzy_blue/Fortuna_circle_horizontal.png?raw=true#gh-light-mode-only" alt="Fortuna" height="200" />
  <hr />
    <h2 align="center" style="border-bottom: none">Bitcoin style proof of work in smart contract form</h2>

[![Licence](https://img.shields.io/github/license/aiken-lang/fortuna)](https://github.com/aiken-lang/fortuna/blob/main/LICENSE)
[![Tests](https://github.com/aiken-lang/fortuna/actions/workflows/tests.yml/badge.svg?branch=main)](https://github.com/aiken-lang/fortuna/actions/workflows/tests.yml)

<hr/>
</div>

## Mining $TUNA

> The current miner is naive and a better implementation is coming soon.

### Requirements

- [Deno](https://deno.land/manual@v1.36.3/getting_started/installation)
- [Kupo](https://cardanosolutions.github.io/kupo/)
- [Ogmios](https://github.com/CardanoSolutions/ogmios)

> You can easily get access to Kupo and Ogmios with
> [Demeter](https://demeter.run). Once you have a project in Demeter you can
> connect Ogmios and Kupo extensions for mainnet. Make sure to toggle
> `Expose http port` in each extensions' settings.

#### Environment variables

Once you have URLs for Kupo and Ogmios, create a `.env` file in the root of the
project with the following content:

```
KUPO_URL="https://<Kupo URL>"
OGMIOS_URL="wss://<Ogmios URL>"
```

#### Wallet

You'll need to create a wallet for the miner which can be done with the
following command:

```sh
deno task cli init
```

Then run the following command to get the miner address:

```sh
deno task cli address
```

You'll need to fund this address with some $ADA to pay for transaction fees.

### Running

After everything is setup, you can run the miner with the following command:

```sh
deno task cli mine
```

### Rust Miner

- works on windows
- works on linux

You can check releases for pre-built binaries/exes but its always best for you to build on your own

CUDA requried to be installed before building. 

Make sure server/stratum is working. This must be already running.


Run server/stratum with
```sh
deno run --allow-all miner/server.ts "mine"
```

binary/executable must be built 

To build you need you need to install:

- [rust](https://www.rust-lang.org/tools/install)

These libraries below for linux (instructions are for ubunutu) 
```shell
sudo apt-get install pkg-config libssl-dev
```
```shell
sudo apt-get install build-essential
```

Go into tuna_cuda_miner directory with
```shell
cd tuna_cuda_miner
```
```shell
cargo build --release
```
binary will be in `/target/release`
```shell
cd /target/release
```

Run with 
```shell
./tuna_cuda_miner <deno server link>
```

Server does not need to be local, it can be remote as such
```shell
./tuna_cuda_miner https://my-aws-server.com
```

If no server is specified it will be `http://localhost:8008` by default

Note: this is a very quick implementation of a CUDA miner. Code is poor quality and could be unstable. 

### Policy

The policy for the TUNA token is
`279f842c33eed9054b9e3c70cd6a3b32298259c24b78b895cb41d91a`
