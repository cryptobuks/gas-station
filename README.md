# ⛽️ Gas Station

**Gas Station is a library for React Native apps to easily connect to the Ethereum network and complete transactions.**

## Description
Gas Station is a React Native library allowing you to build dApps (Decentralized Applications) which transform your mobile device into a light client node on the Ethereum Network and enables you to easily access Ethereum’s entire ecosystem, including interacting with Smart Contracts, make payment, and more.


## Project status
We just got started. This is what the project timeline looks like:

- May 20th: have [react-native-geth](https://github.com/YsnKsy/react-native-geth) up and running for iOS.
- June 10th: finished basic UI for creating a wallet, getting funds, and approving transactions.
- June 20th: finish interface and API for connecting with other apps to share wallets between apps.
- July 1st: added Android support.
- July 10th: first stable release for iOS and Android.


## Supported platforms

* iOS
* _Android support coming soon_


## Installation

Using [NPM](https://npmjs.org/):

```
npm i gas-station
react-native link gas-station
```

Using [Yarn](https://yarnpkg.com/lang/en/docs/yarn-lock/):

```
yarn add gas-station
react-native link gas-station
```


## Compatibility

Due to the rapid changes being made in the React Native ecosystem, we are not officially going to support this module on anything but the latest version of React Native. With that said, we will do our best to stay compatible with older versions as much that is practical, and the peer dependency of this requirement is set to "react-native": "*" explicitly for this reason. If you are using an older version of React Native with this module though, some features may be buggy.


## Usage example

```js
import { Alert } from 'react-native'
import GasStation from 'gas-station'
 
// Do this as soon as you need access to the Ethereum network
// Note that this will bring up a UI the first time it is called!
GasStation.requestUserLogin()
	.then(async (eth) => {
		// We now have access to the ethereum blockcahin
		const addresses = await eth.getAccounts()
		Alert.alert('Your wallet address', addresses[0])
	})
	.catch((e) => {
		// Node couldn't start or user cancelled login
	})
```

## API documentation

All API methods below are asynchronous and return **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)** instances.


### getAccounts

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** denoting the addresses of all wallets that the user has created or has given the current app access to.

### getAddress

Retrieves the address associated with the user's default account.

Returns **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** with wallet address.

### getBalanceAccount

Returns the wei balance of the current account.

Returns **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** balance.

### getBalance

Returns the wei balance of the specified account.

**Parameters**

-   `address` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Address of account being looked up.

Returns **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** balance.

### syncProgress

Retrieves the current progress of the sync algorithm.

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** Return object sync progress or null

### subscribeNewHead

Subscribes to notifications about the current blockchain head.

Returns **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** – true if subscribed.

### showAccounts

Brings up a modal window where the user can manage their accounts.

### showTopUp

Brings up a modal window where the user can add Ethereum to their primary account, either by copying their address, viewing their wallet's QR code, or by opening the Coinbase app and starting a transaction to their wallet's address.

### sendTransaction

Create and send a transaction. The user will see a modal window and will have to agree to sending the transaction.

**Parameters**

-   `toAddress` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Address destination
-   `amount` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** Amount
-   `gasLimit` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** Gas limit (optional, automatically set if left empty)
-   `gasPrice` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** Gas price (optional, automatically set if left empty)
-   `data` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)**

Returns **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** – transaction HEX identifier

### getSuggestedGasPrice

Retrieves the currently suggested gas price to allow a timely execution of a transaction.

Returns **Double** – suggested gas price

### getPendingNonce

Retrieves this account's pending nonce. This is the nonce you should use when creating a transaction.

Returns **Double** – nonce
