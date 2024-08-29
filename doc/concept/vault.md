# Vault (Former WalletSystem)

Is a system that holds many users `wallets`.
The vault is a hosted system, that can be run by a single entity or service provider.

It is responsible for managing the users wallets, their keys, orchestration and signing of transactions.

It simplifies the process of holding granular certificates across multiple registries,
and abstracts away the complexity of slices and streams.

Users can query the vault for their GCs, trasfer them to others or claim consumption and production.

## Remote endpoints

Users can transfer their GCs to other users, by creating a `remote endpoint` by getting a `walletEndpoint` from the other user.

Once this is created the user can transfer GCs to the other user easily and cryptographically secure.

## System documentation

More documentation can be found in the [Vault](../wallet/index.md) project.

![C4 system diagram of the wallet](../wallet/wallet-c4-system.drawio.svg)

## API

The vault has a REST API that can be used to interact with the system.

<script src="https://cdn.redoc.ly/redoc/latest/bundles/redoc.standalone.js"></script>
<redoc spec-url="../wallet/api/open-api.json"></redoc>
