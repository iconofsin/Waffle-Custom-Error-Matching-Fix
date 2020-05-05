[![CircleCI](https://circleci.com/gh/EthWorks/Waffle.svg?style=svg)](https://circleci.com/gh/EthWorks/Waffle)
[![](https://img.shields.io/npm/v/@ethereum-waffle/ens.svg)](https://www.npmjs.com/package/@ethereum-waffle/ens)

![Ethereum Waffle](https://raw.githubusercontent.com/EthWorks/Waffle/master/docs/source/logo.png)

# @ethereum-waffle/ens

A simple ens builder for testing with ENS.

## Installation

In the current version of waffle (v2.x.x) you will install this package as a dependency of the main waffle package - `ethereum-waffle`.

```
yarn add --dev ethereum-waffle
npm install --save-dev ethereum-waffle
```

If you want to use this package directly please install it via:
```
yarn add --dev @ethereum-waffle/ens
npm install --save-dev @ethereum-waffle/ens
```

## Feature overview

**NOTE**: You do not need to use this package directly. You can install it through the main package (`ethereum-waffle`) and use it instead.

### ENSBuilder

The `ENSBuilder` class allows to create ENS domains for testing.

It will deploy ENS smart contracts system to your test node.

To create `ENSBuilder`, you should submit your `wallet`, available in `MockProvider` class in package `@ethereum-waffle/provider`.

You can read more about ENS [in the ENS's documentation](https://docs.ens.domains/).

### Examples:
Creating of ENSBuilder:
```ts
import {MockProvider} from '@ethereum-waffle/provider';
import {createENSBuilder, ENSBuilder} from '@ethereum-waffle/ens';

const provider = new MockProvider();
const [wallet] = provider.getWallets();
const ensBuilder: ENSBuilder = await createENSBuilder(wallet);
```

### Usage

Use `createTopLevelDomain` function to creating top level domain:

```ts
await ensBuilder.createTopLevelDomain('test');
```

Use `createSubDomain` function to creating sub domain for exiting domain:

```ts
await ensBuilder.createSubDomain('ethworks.test');
```

And use `setAddress` function for setting address for existing domain:

```ts
await ensBuilder.setAddress('vlad.ethworks.test', '0x001...03');
```