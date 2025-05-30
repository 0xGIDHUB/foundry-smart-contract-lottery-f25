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
- Setup a .env file containing the anvil wallet private key:
```
DEFAULT_ANVIL_KEY=0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
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
