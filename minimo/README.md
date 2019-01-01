# Minimo

Mimo v1 aka "Minimo" is a minimal version of Mimo which only has support one profile per account (your Ethereum address is your unique ID). Minimo will be our MVP until we test our assumptions concerning e-contracts and how people will use the Mimo protocol.

## Methods

### Querying
There are several methods for querying data in Minimo, most are done by supplying a unique ID (your Ethereum address in this case). You can:

- get all profiles
- get a specific profile (supply address)
- get several profiles* (supply name)
- check if a name is already taken by another profile** (supply name)
- get a specific profile (supply emoji set)
- resolve an ENS name*** (supply ENS name)

- 1: Since any profile can register with any name, getting profiles by name might return several profiles.

- 2: If getting profile by name returns an array with at least one entry, we know that a certain name has been taken already.

- 3: By getting the owner of an ENS name with web3, we can find which address to query our profile with.

### Modifying
There is only one method for modifying data in Minimo, called `updateProfile(signature: String, data: String)`. It accepts a JSON.stringify-ied object as `data` and a `signature` of the data (hashed).

The stringify-ied object is parsed by the MimoStore itself so developers only need to supply a string and whatever new data they want to add to a profile, the MimoStore handles all the indexing itself.

## Components

### MimoStore
MimoStore is a custom OrbitDB store that allows users to interact with the Mimo protocol. It extends the standard KeyValueStore to accept cryptographic signatures for data modification. To update your profile, simply sign a change you want to submit.

```sh
npm install mimostore
```

### Mimo.js
Mimo.js is a javascript library that helps developers obtain data from the deployed MimoStore instance. With Mimo.js, developers can fetch any profile's public information or update a profile's information simply. Supply an ipfs instance in the constructor and the db is generated itself.

```sh
npm install ethmimo
```

### Mimo-ql
Mimo-ql is a starter kit for quickly setting up a graphql server with support for Mimo. Supplying an ipfs instance in the constructor will open a graphql server complete with the appropriate resolver functions.

```sh
npm install mimo-ql
```
