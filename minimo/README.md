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
