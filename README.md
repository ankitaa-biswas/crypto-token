# Crypto Token

This project implements a simple cryptocurrency token on the Internet Computer (IC) using Motoko for the backend and React for the frontend.

## Features
- Token distribution through a faucet.
- Balance checking.
- Secure token transfers between users.

## Prerequisites
- Install DFINITY SDK: [DFINITY SDK](https://smartcontracts.org/docs/developers-guide/install-upgrade-remove.html)
- Install Node.js and npm.

## Setup
1. Clone the repository:
   ```sh
   git clone https://github.com/ankitaa-biswas/crypto-token.git
   cd crypto-token
   ```

2. Install dependencies:
   ```sh
   npm install
   ```

3. Start the DFINITY local replica:
   ```sh
   dfx start --background
   ```

4. Deploy the canisters:
   ```sh
   dfx deploy
   ```

## Usage


# Check your Balance

1. Find out your principal id:

```
dfx identity get-principal
```

2. Save it somewhere.



3. Format and store it in a command line variable:
```
OWNER_PUBLIC_KEY="principal \"$( \dfx identity get-principal )\""
```

4. Check that step 3 worked by printing it out:
```
echo $OWNER_PUBLIC_KEY
```

5. Check the owner's balance:
```
dfx canister call token_backend balanceOf "( $OWNER_PUBLIC_KEY )"
```



### Claim Free Tokens
1. Call the faucet to receive tokens:
   ```sh
   dfx canister call token_backend payOut
   ```

### Transfer Tokens
1. Transfer tokens to another user:
   ```sh
   dfx canister call token_backend transfer '(principal "<recipient-id>", amount)'
   ```





# Charge the Canister

1. Check canister ID:
```
dfx canister id token_backend
```

2. Save canister ID into a command line variable:
```
CANISTER_PUBLIC_KEY="principal \"$( \dfx canister id token_backend )\""
```

3. Check canister ID has been successfully saved:
```
echo $CANISTER_PUBLIC_KEY
```

4. Transfer half a billion tokens to the canister Principal ID:
```
dfx canister call token_backend transfer "($CANISTER_PUBLIC_KEY, 500_000_000)"
```

