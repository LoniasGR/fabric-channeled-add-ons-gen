# Fabric Channeled Add-ons Gen

**fabric-channeled-add-ons-gen** is an open-source generator for Hyperledger Fabric add-on apps in dedicated channels.
Inspired by the increasing utilization of browser extensions, **fabric-channeled-add-ons-gen** provides a solution
for deploying user management applications on different Hyperledger Fabric channels in the form of add-ons.

## Application

TBD

## Extension

TBD

## Smart Contract

The smart contract (in folder `chaincode`) is written in GO
and implements the following functions to support the application:

- CreateAsset
- ReadAsset
- UpdateAsset
- DeleteAsset
- TransferAsset

Note that the asset transfer implemented by the smart contract is a simplified scenario, without ownership validation, meant only to demonstrate how to invoke transactions.

## Running the sample

The Fabric test network is used to deploy and run this sample. Follow these steps in order:

1. Create the test network and a channel (from the `test-network` folder).

   ```bash
   ./network.sh up createChannel -c mychannel -ca
   ```

2. Deploy one of the smart contract implementations (from the `test-network` folder).

   ```bash
   ./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go/ -ccl go
   ```

3. Run the application (from the `fabric-channeled-add-ons-gen` folder).

   ```bash
   cd application
   npm install
   npm start
   ```

## Clean up

When you are finished, you can bring down the test network (from the `test-network` folder). The command will remove all the nodes of the test network, and delete any ledger data that you created.

```bash
./network.sh down
```

## Status & Credits

- Initial version supports an **asset-transfer-basic** workflow on **Google Chrome**.
- Inspired by https://github.com/hyperledger-labs/fabric-chrome-extension.
