
<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">


  <h3 align="center">Foundry FundMe</h3>

  <p align="center">
    A crowdsourcing DAPP built to deploy on Ethereum.
    <br />
    <a href="https://github.com/0x5am/foundry-fund-me"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/0x5am/foundry-fund-me">View Demo</a>
    ·
    <a href="https://github.com/0x5am/foundry-fund-me/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
    <a href="https://github.com/0x5am/foundry-fund-me/issues/new?labels=enhancement&template=feature-request---.md">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#deploy">Deploy</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

This project was created in conjunction with Patrick Collins as part of Cyfrin's Updraft solidity course. This is a simple smart contract which allows crowdsourcing on the Ethereum mainnet. 

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With

This section should list any major frameworks/libraries used to bootstrap your project. Leave any add-ons/plugins for the acknowledgements section. Here are a few examples.

* [![Solidity][Solidity.logo]][Solidity-url]


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started
### Prerequisites
* [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  * If you have correctly installed git you should see a response similar to the one below when you run ```git --version  ```
    ```sh
    git --version
    git version x.x.x
    ```
* [foundry](https://getfoundry.sh/)
  * If you have correctly installed git you should see a response similar to the one below when you run ```forge --version  ```
    ```sh
    forge --version
    forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)
    ```
### Installation


1. Clone the repo
   ```sh
   git clone https://github.com/0x5am/foundry-fund-me
   ```
2. Navigate to the repo
   ```sh
   cd foundry-fund-me
   ```
3. Execute the makefile
   ```sh
   make
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage
### Deploy
```sh
forge script script/DeployFundMe.s.sol
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Local ZkSync Deployment -->
### Local zkSync Deployment
The following instructions will allow you to work with this repository in zkSync.
#### (Additional) Requirements
In addition to the requirements above, you will also need:
* [foundry-zksync](https://github.com/matter-labs/foundry-zksync)
  * If you have correctly installed git you should see a response similar to the one below when you run ```forge --version  ```
    ```sh
    forge --version
    forge 0.0.2 (816e00b 2023-03-16T00:05:26.396218Z)
    ```

* [npx & npm](https://docs.npmjs.com/cli/v10/commands/npm-install)
  * * If you have correctly installed git you should see a response similar to the one below when you run ```npm --version  ```
    ```sh
    npm --version
    8.1.0
    ```
* [docker](https://docs.docker.com/engine/install/)
  * If you have correctly installed git you should see a response similar to the one below when you run ```docker --version  ```
    ```sh
    docker --version
    Docker version 20.10.7, build f0df35
    ```
  * To make sure the daemon is running correctly you should see a similar response when you run ```sh docker --info ```
    ```sh
    Client:
      Context:    default
      Debug Mode: false
    ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

#### Setup local zkSync node
Run the following commands:
```sh
npx zk-sync-cli dev config
```
Select ``` In memory node ``` and do not select any additional modules.
Then run the following command:
```sh
npx zksync-cli dev start
```
If done correctly, you should see an output similar to the following:
```sh
In memory node started v0.1.0-alpha.22:
 - zkSync Node (L2):
  - Chain ID: 260
  - RPC URL: http://127.0.0.1:8011
  - Rich accounts: https://era.zksync.io/docs/tools/testing/era-test-node.html#use-pre-configured-rich-wallets
```

#### Deploy to local zkSync node
```sh
make deploy-zk
```
This will deploy a mock price feed and fund me contract to the zkSync node using a custom makefile shortcut.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Deployment to a testnet or mainnet
1. Set up your environment variables 
  * You'll want to set your ```TESTNET_RPC_URL``` and ```PRIVATE_KEY``` as environment variables in a .env file.
    * ```PRIVATE_KEY```: The private key of your account/wallet (like [MetaMask](https://support.metamask.io/managing-my-wallet/secret-recovery-phrase-and-private-keys/how-to-export-an-accounts-private-key/), for example). **NOTE:** THIS IS FOR <u>DEVELOPMENT PURPOSES ONLY</u>, PLEASE DO NOT USE AN ACCOUNT THAT HAS ANY REAL FUNDS ASSOCIATED.
    * ```TESTNET_RPC_URL```: This should be the url of whatever testnet node you are working with. This project was tested on the Seplolia testnet, you can set up one for free with [Alchemy](https://www.alchemy.com/).
    * Optionally, you can add your ```ETHERSCAN_API_KEY``` if you wish to verify your contract on [Etherscan](https://etherscan.io/).
2. Get testnet ETH
  * Head over to any faucet ([Chainlink](https://faucets.chain.link/), [Google](https://cloud.google.com/application/web3/faucet/ethereum), [Alchemy](https://www.alchemy.com/faucets/ethereum-sepolia)). After  a few minutes the testnet ETH should appear in your wallet.
3. Deploy using the following command:
```
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
```
#### Scripts
After deploying to a testnet or local net, you will be able to run the scripts.
This can be done using cast when deployed locally:
```
cast send <FUNDME_CONTRACT_ADDRESS> "fund()" --value 0.1ether --private-key <PRIVATE_KEY>
```
or 
```
forge script script/Interactions.s.sol:FundFundMe --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast
forge script script/Interactions.s.sol:WithdrawFundMe --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast
```

#### Withdraw
```
cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()"  --private-key <PRIVATE_KEY>
```

#### Estimate gas
You can estimate how much gas each of your functions cost by running the following command:
```
forge snapshot
```
If done correctly, you will see an output file called ```.gas-snapshot```.
<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Sam Cheetham - [@_0x5am](https://x.com/_0x5am_)

Project Link: [https://github.com/your_username/repo_name](https://github.com/your_username/repo_name)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/0x5am/foundry-fund-me.svg?style=for-the-badge
[contributors-url]: https://github.com/0x5am/foundry-fund-me/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/0x5am/foundry-fund-me.svg?style=for-the-badge
[forks-url]: https://github.com/0x5am/foundry-fund-me/network/members
[stars-shield]: https://img.shields.io/github/stars/0x5am/foundry-fund-me.svg?style=for-the-badge
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/0x5am/foundry-fund-me.svg?style=for-the-badge
[issues-url]: https://github.com/0x5am/foundry-fund-me/issues
[license-shield]: https://img.shields.io/github/license/0x5am/foundry-fund-me.svg?style=for-the-badge
[license-url]: https://github.com/0x5am/foundry-fund-me/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/sam-cheetham-b8a58b1a5/
[Solidity.logo]: https://img.shields.io/badge/solidity-%5E0.8.0-orange
[Solidity-url]: https://soliditylang.org/
