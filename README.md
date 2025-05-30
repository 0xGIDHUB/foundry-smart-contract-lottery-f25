# Raffle OnChain (Chainlink Automated)

An Onchain Enabled Lottery

## Description

Raffle Onchain is a project built with solidity and foundry. It enables users to enter a lottery for a set duration of time after which a winner is picked and given the lottery prize. This variation of the raffle project uses Chainlink Automations to pick a winner without having to call a function in the raffle smart contract.

## Getting Started

### Requirements

* [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  * You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
* [foundry](https://getfoundry.sh/)
  * You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`

### Dependencies

* Foundry Devops version 0.2.2
* Chainlink Brownie Contracts version 1.1.1
* Solmate v6

### Installation

- All commands are expected to be run on a WSL shell for windows users

#### Clone the repo
- Run the following commands
```
git clone https://github.com/0xGIDHUB/foundry-smart-contract-lottery-f25
cd foundry-smart-contract-lottery-f25
```
#### Install make
- Run the command
```
sudo apt install make
```

#### Install dependencies
- Run the command
```
make install
```

### Deploying On Sepolia
- Setup a .env file containing your sepolia rpc url and etherscan api key:
```
SEPOLIA_RPC_URL=pasteyoursepoliarpcurlhere
ETHERSCAN_API_KEY=pasteyouretherscanapikeyhere
```
Run the command:
```
source .env
```
- Setup your cast wallet by running the command:
```
cast wallet import -i
```
(You will be prompted to input your private key from your web3 wallet e.g metamask)
- To deploy the raffle smart contract to sepolia testnet run:
```
make deploy-sepolia
```

You can checkout a deployed raffle smart contract on [etherscan](https://sepolia.etherscan.io/address/0xDE337A784Bdc0857eE7cF61e8145E96728081c44#code)


### Deploying On Local Anvil
- Setup an anvil node on your terminal, run:
```
anvil
```
- You should get an output like this:
```
                             _   _
                            (_) | |
      __ _   _ __   __   __  _  | |
     / _` | | '_ \  \ \ / / | | | |
    | (_| | | | | |  \ V /  | | | |
     \__,_| |_| |_|   \_/   |_| |_|

    1.0.0-stable (e144b82070 2025-02-13T20:03:31.026474817Z)
    https://github.com/foundry-rs/foundry

Available Accounts
==================

(0) 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 (10000.000000000000000000 ETH)
(1) 0x70997970C51812dc3A010C7d01b50e0d17dc79C8 (10000.000000000000000000 ETH)
(2) 0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC (10000.000000000000000000 ETH)
(3) 0x90F79bf6EB2c4f870365E785982E1f101E93b906 (10000.000000000000000000 ETH)
(4) 0x15d34AAf54267DB7D7c367839AAf71A00a2C6A65 (10000.000000000000000000 ETH)
(5) 0x9965507D1a55bcC2695C58ba16FB37d819B0A4dc (10000.000000000000000000 ETH)
(6) 0x976EA74026E726554dB657fA54763abd0C3a0aa9 (10000.000000000000000000 ETH)
(7) 0x14dC79964da2C08b23698B3D3cc7Ca32193d9955 (10000.000000000000000000 ETH)
(8) 0x23618e81E3f5cdF7f54C3d65f7FBc0aBf5B21E8f (10000.000000000000000000 ETH)
(9) 0xa0Ee7A142d267C1f36714E4a8F75612F20a79720 (10000.000000000000000000 ETH)

Private Keys
==================

(0) 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
(1) 0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d
(2) 0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a
(3) 0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6
(4) 0x47e179ec197488593b187f80a00eb0da91f1b9d0b13f8733639f19c30a34926a
(5) 0x8b3a350cf5c34c9194ca85829a2df0ec3153be0318b5e2d3348e872092edffba
(6) 0x92db14e403b83dfe3df233f83dfa3a0d7096f21ca9b0d6d6b8d88b2b4ec1564e
(7) 0x4bbbf85ce3377467afe5d46f804f221813b2bb87f24d81f60f1fcdbf7cbf4356
(8) 0xdbda1821b80551c9d65939329250298aa3472ba22feea921c0cf5d620ea67b97
(9) 0x2a871d0798f97d79848a013d4936a73bf4cc922c825d33c1cf7073dff6d409c6

Wallet
==================
Mnemonic:          test test test test test test test test test test test junk
Derivation path:   m/44'/60'/0'/0/


Chain ID
==================

31337

Base Fee
==================

1000000000

Gas Limit
==================

30000000

Genesis Timestamp
==================

1748638531

Listening on 127.0.0.1:8545
```
- Setup a .env file containing the anvil rpc and wallet private key:
```
ANVIL_RPC_URL=http://127.0.0.1:8545
DEFAULT_ANVIL_PRIVATE_KEY=0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
```
Run the command:
```
source .env
```
- To deploy the raffle smart contract to local Anvil blockchain run:
```
make deploy-anvil
```
> **Note**  
> I had to resolve an arithmetic overflow/underflow error when deploying to anvil so if you get a similar error, locate the createSubscription function in the SubscriptionAPI.sol contract inherited by the VRFCoordinatorV2_5.Mock.sol and change the following code block..:
>
> ```subId = uint256(keccak256(abi.encodePacked(msg.sender, blockhash(block.number-1), address(this), currentSubNonce)));```
>
>..to this:
>
> ```subId = uint256(keccak256(abi.encodePacked(msg.sender, blockhash(block.number), address(this), currentSubNonce)));```




## Author

Gideon Ov  
Twitter: [@0xGIDHUB](https://x.com/0xGIDHUB)


## License

This project is licensed under the MIT License

## Acknowledgments
Much thanks to [Patrick Collins](https://x.com/PatrickAlphaC) and [Cyfrin Updraft](https://www.cyfrin.io/updraft) for providing the learning resources for this project.
