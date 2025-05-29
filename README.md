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

### Deploying
- Setup a .env file containing your sepolia rpc url and etherscan api key before deployment, run:
```
source .env
```
- Setup your cast wallet by running the command:
```
cast wallet import -i
```
(You will be prompted to input your private key)
- To deploy the raffle smart contract to sepolia testnet run:
```
make deploy
```

You can checkout a deployed raffle smart contract on [etherscan](https://sepolia.etherscan.io/address/0xDE337A784Bdc0857eE7cF61e8145E96728081c44#code)


## Author

Gideon Ov  
Twitter: [@0xGIDHUB](https://x.com/0xGIDHUB)


## License

This project is licensed under the MIT License

## Acknowledgments
Much thanks to [Patrick Collins](https://x.com/PatrickAlphaC) and [Cyfrin Updraft](https://www.cyfrin.io/updraft) for providing the learning resources for this project.
