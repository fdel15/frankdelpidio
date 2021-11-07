+++
title = "Proof of Burn"
date = 2021-09-24T14:56:54-04:00
images = []
tags = ["plutus", "whitepaper", "tutorial"]
categories = []
draft = true
+++

<!-- Abstract of what the article is about
  - Define Proof of Burn Protocol
  - Potential use cases
  - Possible implementation according to IOHK white paper
 -->
 Proof of burn is a mechanism to permanently destroy cryptocurrency coins in a verifiable manner. This post will discuss potential use cases for proof of burn, properties of the protocol from the [IOHK research paper](https://eprint.iacr.org/2019/1096.pdf), and an implementation of the protocol using a Cardano smart contract.

## Why would you want to burn your cryptocurrency?

This is a valid question that most people ask when learning about proof-of-burn. The following are a non-exhausitve list of use cases for the proof-of-burn protocol.

### Decrease the supply of coins

In a YouTube video [SOURCE], Charles Hoskinson said that he is frequently asked to burn ADA by speculators who own the cryptocurrency in their own wallet. These speculators want to decrease the supply of outstanding ADA coins so that the value of each coin they possess increases.

You can calculate the price of a coin by doing basic division:

market cap of crypto currency / number of coins in circulation = price per coin

If a crypto currency has a market cap of $100 and there are 100 coins in circulation, then each coin is worth $1. 

$100 / 100 coins = $1 per coin

If 50 coins are burned, then each coin that was not burned will double in value to $2.

$100 / 50 coins = $2 per coin

It is important to note that there was no value created or lost during the burning process. The market cap is still $100. Half of the coins are worth $1 more only because the other half of the coins are worth $1 less. Value is lost from the burned coins and redistributed to the surviving coins.

In Cardano's case, there are over 32 billion coins in circulation, and the current market cap is about $72 billion at the time of this writing. A lot of coins would need to be burned to significantly affect the price of an individual coin.

### Bootstrap A Crypto Currency
The [IOHK research paper](https://eprint.iacr.org/2019/1096.pdf) discusses using proof-of-burn to bootstrap a new cryptocurrency.

The paper describes a chicken and the egg problem for new cryptocurrencies. In order for a cryptocurrency to gain traction, it needs to be listed on exchanges that allow people to buy and sell the cryptocurrency. However, when a cryptocurrency is new, it is difficult to get listed on an exchange because of the lack of traction.

The proposed solution utilizes proof-of-burn to allow a user to gain coins in a target currency by burning coins in a legacy currency. This solution is implemented in the [IOHK research paper](https://eprint.iacr.org/2019/1096.pdf) using a solidity contract. By burning coins in the legacy currency, users are able to demonstrate they are invested in the new currency.

### Other Use Cases
The paper briefly mentions other use cases for proof of burn, and while the use cases may still be viable, the specific references no longer appear to be in use.

Slimcoin was a peer-to-peer cryptocurrency that attempted to use proof-of-burn as part of their consensus mechanism. The details can be found in their [white paper](https://slimcoin.info/whitepaperSLM.pdf)

OpenBazaar, the decentralized marketplace, used proo-of-burn to implement a [reputation system](https://www.openbazaar.org/blog/proof-of-burn-and-reputation-pledges/) to add a layer of trust to their platform.

 <!-- Components of protocol 
   - function to generate a cryptocurrency where coins will be addressed if sent here
   - verification function that checks an address is really unspendable
   - protocol properties:
     - unspendability
     - binding
     - uncensorability
 -->
 ## How Proof Of Burn works

Proof of burn can be implemented in different ways. The [IOHK research paper](https://eprint.iacr.org/2019/1096.pdf) describes an implementation that can work with many different blockchains. 

The proof of burn protocol has the following properties:

  - Unspendability

  Once a coin is burned, it can no longer be spent.

  - Binding

  There needs to be a way to verify that a coin was burned. To acheive this, a tag is provided as metadata during the burning process. The binding property ensures that the burn commits to only a single metadata tag.

  - Uncensorability

  Burning coins is a transaction that needs to be validated on the network like any other transaction. In order to prevent miners refusing to validate burn transactions, the protocol needs to make the "burn address" look like any other valid address on the network to make it difficult for miners to identify and refuse burn transactions.


Let's walk through a use case to see how it works.

Alice decides she wants to burn 100 ADA coins. To burn the coins, she needs to send them somewhere on the blockchain that gurantees they will never be spent. This is called a "burn address". 

Alice is able to generate a burn address directly from her wallet. She provides a tag for the bidning process mentioned above, and this tag is encoded into the address that is generated.

Finally Alice sends the 100 ADA from her wallet to the burn address. She is able to verify that the coins were burned by providing

Smart Contract that






#### Unspendability

### CreateBurnAddress

The first function that the protocol relies on is a function to create 

 <!-- Implementation 
   - GenBurAddr
      - importance of meta tag
   - SpendVerifi
      - performed by smart contract to confirm that ada was burned
      - mints NFT and sends to user as proof of burn
 -->