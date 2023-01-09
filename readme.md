# Gas Cost Profiler

This repository contains a high-level Gas Cost Profiler for Ethereum smart contracts.
Our Node.js tool takes a transaction hash as input and generates a cost profile from the executed opcode trace.

## Requirements
Node.js must be installed.
Access to an Ethereum archive node is required in order to get execution traces. Free access can be requested from the [ArchiveNode](https://archivenode.io/) team. The archive node url must be inserted in the ```TraceController.js``` file as value for the variable ```archive_node_url```.

## Startup
For installation, open the folder location in a command line and run the ```npm install``` command.
Afterwards run ```npm start``` to start the local node.js web application.
Per default, the server starts on ```localhost:8002``` but you can customize these settings in the ```index.js``` file.

## Usage
Now you can use e.g. [Postman](https://www.postman.com/) or your browser to query the cost profile for a transaction.
To use the cost profiler in your browser, just open the URL ```localhost:8002/analyze/<txHash>```.
For testing purposes browse the [Etherscan](https://etherscan.io/txs) blockchain explorer, select a transaction and call the local profiler url with the transaction hash.

## Example
Transaction [0x2319b4a7817fa870213412b9f90b114cd2081bc77a53b909e031e2969ba09c51](https://etherscan.io/tx/0x2319b4a7817fa870213412b9f90b114cd2081bc77a53b909e031e2969ba09c51)

Request
```
GET localhost:8002/analyze/0x2319b4a7817fa870213412b9f90b114cd2081bc77a53b909e031e2969ba09c51
```

Response
```JSON
{
    "hash": "0x2319b4a7817fa870213412b9f90b114cd2081bc77a53b909e031e2969ba09c51",
    "gasUsed": 256667,
    "gasLimit": 318730,
    "sender": "0x080597ddc25abbac505d127cb09b5e38f8095661",
    "receiver": "0x2af47a65da8cd66729b4209c22017d6a5c2d2400",
    "baseFee": 24008,
    "calculation": 1750,
    "communication": 477,
    "external": 24375,
    "logging": 3905,
    "storage": 202152,
    "maxDepth": 2
}
```

## Publication
This tool was presented and used in the following [ICSME'22 paper](https://doi.org/10.1109/ICSME55016.2022.00034).

> B. Severin, M. Hesenius, F. Blum, M. Hettmer and V. Gruhn, "Smart Money Wasting: Analyzing Gas Cost Drivers of Ethereum Smart Contracts," 2022 IEEE International Conference on Software Maintenance and Evolution (ICSME), 2022, pp. 293-304, doi: 10.1109/ICSME55016.2022.00034.
