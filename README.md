<p align="center">
	<img src="https://raw.githubusercontent.com/eoscostarica/proton-affiliate/main/docs/img/proton-xpr-logo.png" width="200" >
</p>

<p align="center">
	<a href="#">
		<img src="https://img.shields.io/dub/l/vibe-d.svg" alt="MIT">
	</a>
</p>

## Description
This project builds the Proton network in a local environment so that testing can be done before being published on the public network.

### Why to use a local environment?
Having a local environment provides a series of benefits that you cannot in a public network, for example, with Proton locally, transaction costs are avoided since they are carried out in a development environment and not in production, also, they are accessed to system contracts to modify them as appropriate.

In a Blockchain network every transaction creates an immutable record and everything that is modified can affect both positively and negatively the users within it, it is for this reason that it is essential to have an environment premises where functionality tests, performance tests, stress tests, among others, can be carried out without the risk of producing a failure that affects users.

Finally, a factor to consider is the time that is reduced in the initial configuration of any network, this image allows directly, with only two commands to have the network installed and ready to perform functionality tests as necessary.

### Contracts
The Proton image is based on the `eosio.proton`, `token.proton` and `cfund.proton` contracts for its governance configuration. Your code can be found at [this link](https://github.com/ProtonProtocol/proton.contracts/tree/master/contracts). Additionally, the following contracts are required as part of the full setup process:
1. **eosio.system**: Provides the governance rules established by the Proton network.
2. **eosio.token**: Defines the structures and actions that allow users to create, issue, and manage tokens for EOSIO-based blockchains.
3. **eosio.msig**: Allows the creation of proposed transactions that require authorization from a list of accounts.

### Configuration key
The preconfigured key is the eosio key that allows you to carry out the initial configuration of the network. You can consult it [here](https://github.com/eoscostarica/proton-local/blob/main/Dockerfile#L38).
```
EOSIO_PRIVATE_KEY: 5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3
EOSIO_PUBLIC_KEY:  EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
```

### Prerequisites
- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/en/)
- [Docker](https://www.docker.com/)
- [Eosio](https://developers.eos.io/welcome/latest/getting-started-guide/local-development-environment/index)

## Quick start
- Download the Docker image `docker pull eoscostarica506/proton-local`
- Run the Docker image `docker run -dp 8888:8888 eoscostarica506/proton-local`
- Run the command `cleos get info` or check the link in the browser `http://127.0.0.1:8888/v1/chain/get_info`

If you run the command `cleos get info` or go to` http://127.0.0.1:8888/v1/chain/` and get information like the following it is because you already have the environment ready to work.

```
{"server_version":"e57a1eab","chain_id":"981453d176ddca32aa278ff7b8af9bf4632de00ab49db273db03115705d90c5a","head_block_num":66,"last_irreversible_block_num":65,"last_irreversible_block_id":"00000041fcc36403c71cebfc95810f610412b474f60735639fcaa2d241fe5ffa","head_block_id":"00000042a08478812c642d311f5ff22b9212559eeb9ee1042925742d8b46dd7f","head_block_time":"2021-07-08T05:48:45.500","head_block_producer":"eosio","virtual_block_cpu_limit":213407,"virtual_block_net_limit":1118998,"block_cpu_limit":199900,"block_net_limit":1048576,"server_version_string":"v2.0.12","fork_db_head_block_num":66,"fork_db_head_block_id":"00000042a08478812c642d311f5ff22b9212559eeb9ee1042925742d8b46dd7f","server_full_version_string":"v2.0.12-e57a1eab619edffc25afa7eceb05a01ab575c34a"}
```

## Instructions for creating Proton image locally
To create the Docker image locally, you must run the following commands:
- Clone the local Proton repository `https://github.com/eoscostarica/proton-local`
- Enter the cloned repository folder `cd <path/proton-local>`
- Build the Dockerfile image `docker build -t proton-local .`
- Run the Dockerfile image `docker run -dp 8888:8888 proton-local`
- Run the command `cleos get info` or check the link in the browser `http://127.0.0.1:8888/v1/chain/get_info`

By this point, you already have the Proton network image running locally.

## File structure
```text title="./proton-local"
/
├── .github
│   └── workflows
│       └── publish-docker-image.yml
├── config.ini ............... Nodeos configuration file
├── Dockerfile ............... Contains instructions for building the Proton image
├── genesis.json ............. Specifies the network genesis node parameters
├── LICENSE .................. Terms and Conditions
├── README.md ................ Repository specification
└── start.sh ................. Instructions for configuring contracts and usage characteristics
```

## License
MIT © [EOS Costa Rica](https://eoscostarica.io/)

## Contributing
If you want to contribute to this repository, please follow the steps below:

1. Fork the project
2. Create a new branch (`git checkout -b feat/sometodo`)
3. Commit changes (`git commit -m '<type>(<scope>): <subject>'`)
4. Push the commit (`git push origin feat/sometodo`)
5. Open a Pull Request

Read the EOS Costa Rica open source [contribution guidelines](https://guide.eoscostarica.io/docs/open-source-guidelines/) for more information on scheduling conventions.

If you find any bugs, please report them by opening an issue at [this link](https://github.com/eoscostarica/proton-local/issues).


## What is Proton?
Proton is trying to improve and streamline the verification and speed at which payments are processed either between banks or merchants. Currently for traditional payments, users aren’t asked for consent before a payment is processed, unless going over a comfortable limit, from the credit card processor, and the second layer of authentication is usually an insecure telecom network.

Cryptocurrency has no native compliance tools for anti-money laundering, identity, source of funds, or risk scoring for financial institutions to adopt it.

Previously, there wasn’t a way to push or pull funds (or for legacy finance to interact with crypto finance) in real time on the blockchain from credit/debit/ACH/IBAN.

Proton solves this problem by integrating identity verification.

But beyond being an app platform with an unified identity model, the Proton blockchain was designed to allow websites and apps to push payment requests directly to Proton-compliant wallets.

Proton will solve this problem by creating a namespace that works across multiple payment providers, identity verifiers, and payment transmitters. Gone are the days of entering your bank password or credit card number online; crypto and fiat wallets alike now interact as one network to streamline the process of making and receiving payments.

## About EOS Costa Rica
<br>
<center>
<img src="https://raw.githubusercontent.com/eoscostarica/design-assets/master/logos/eosCR/fullColor-horizontal-transparent-white.png" width="400" >
</center>
<br>

EOS Costa Rica is an independently-owned, self-funded, bare-metal Genesis block producer that provides stable and secure infrastructure for EOSIO blockchains. We support open source software for our community while offering enterprise solutions and custom smart contract development for our clients.

[eoscostarica.io](https://eoscostarica.io/)