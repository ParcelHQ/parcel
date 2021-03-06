# Parcel - Simplifying crypto treasury management
Parcel is a decentralized crypto treasury management service with built-in end-to-end data encryption using Gnosis Safe, Filecoin & IPFS.

<img src="https://images-parcel.fra1.digitaloceanspaces.com/dashboard.png" width="100%">

## Problem 

1. Collborative friction in user experience.

2. Payroll & Mass payouts are expensive

3. Data Centralisation

5. Error Prone Accounting

## Solution
1. One Click Mass Payouts 

2. Significantly Cost Efficient Transactions (~ 40% cheaper)

3. Automated recurring payments.

4. Yield Optimisation

5. Built in data privacy on top of distributed database viz. IPFS & Filecoin.

6. Integrated accounting using CSV exports & industry standard tools like quickbooks & xero.


## Website
**[https://parcel.money](https://parcel.money)**

### Components

1. **[Parcel UI](https://github.com/ParcelHQ/parcel-frontend-app/tree/public-data-release)**: Contains the UI for the application. Built with Reactjs, Ether.js, Emotion, & Reactstrap.

2. **[Parcel SDK](https://github.com/ParcelHQ/parcel-sdk)**: Includes all the methods to interact with IPFS gateway via end to end encryption and this component is being used on the client-side with Parcel UI.

3. **[Parcel Filecoin Archiving](https://github.com/ParcelHQ/parcel-filecoin-archiving)**: It includes the code for getting the IPFS hashes from smart contracts and fetch the data from IPFS and archive it on Filecoin using Textile's Powergate. The main purpose of this component is to make sure data is persisted on Filecoin. In case the data is unavailable on IPFS, it can retrieve the data from Filecoin and push it back to IPFS.

## How It's Made

### Tech Stack

1. Asset Management using Gnosis safe.
2. Uniswap for token swapping
3. IPFS for encrypted data storage.
4. Fleek for website hosting.
5. Textile's Powegate for encrypted data archiving on Filecoin.
6. Ethereum signature for generating encryption keys deterministically.
7. Metamask for wallet management.
8. Matic Network for onchain optimization and scalability of E2EE business logic. 
9. Biconomy for network agnostic Meta Transactions i.e without changing layer1 rpc provider on Metamask.

### How are we using IPFS & Filecoin
We are using IPFS in multiple ways to build a highly open and verifiable treasury management system.

1. Parcel's app UI will be hosted on IPFS as well on our servers to avoid single point of Failure and we will be using Fleek for that.
2. We are also using IPFS for our data layer i.e all the company data will be end to end encrypted using ethereum private keys & deterministic signatures and will be stored on IPFS. 

   Moreover, in order to provide complete ownership of the data, all the IPFS CID hashes will be stored in a smart contract as an index so that if Parcel does not    exist tomorrow, users  can still retrieve the data and decrypt that using ethereum private keys. 


   Also, to persist the data for long term we will using Filecoin storage using Textile's powergate.

3. For every new release of our app, we will be publishing it to IPFS for the community to verify it.



Now Let's understand the workflow for adding, getting and updating a user's data and documents.

### Adding Data

1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm.
2. Encrypt data with the generated key.
3. Calculate the master hash from IPFS for the particular section e.g "Documents" in an organization and attach encrypted data to this master hash and then store it in a matic smart contract by doing a transaction and map it to index.

### Getting data

1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm.
2. Fetch the IPFS hashes from the matic smart contract.
3. Get the encrypted data from the IPFS.
4. Decrypt the data locally with the generated key.

### Updating data

1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm.
2. Fetch the IPFS hashes from the smart contract.
3. Get the encrypted data from the IPFS.
4. Decrypt the data locally with the generated key.
5. Encrypt the updated data with the generated key.
6. Calculate the master hash for the updated encrypted data from IPFS and then store it in a matic smart contract by creating a transaction and mapping it to the same index.

## References
1. Filecoin launchpad demo day - https://www.youtube.com/watch?v=z3UaRU0j8Vg&ab_channel=Filecoin
2. Blog - https://medium.com/parcelhq/simplifying-crypto-payroll-at-scale-39c91afd1e9b











