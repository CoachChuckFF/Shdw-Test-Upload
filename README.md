# SHDW Test Upload

## Problem 
Hey team, I'm running into some issues with the API. I keep getting a 401, and I've triple-checked everything is formatted correctly.

My assumption is the FormData is misformatting something. As this FormData only takes an optional string as a third parameter, not an object where you specify filename and contentType as per the docs.

The output of `console.log(signedMessage);` is:

```json
{
    "storageAccount": "FR9UETvWqw4YrxnrjrxJDGpjrpYmcg1UTDiKF99XSAsS",
    "signer": "6jkSFmqT9Pa2s7rFSAsjGbGCKCxfxYreMHcpoTHyM6HA",
    "signature": "uHW6Tp4SZ7gWfxZQqhzCrbfPF4gaC4gz1UA6mqQvkdYED1FAa52zaPaapsexc8UXhRNvua2pLeADr5pVefikmVr",
    "message": "ShdwDrive Signed Message:\nStorage Account: FR9UETvWqw4YrxnrjrxJDGpjrpYmcg1UTDiKF99XSAsS\nUpload files with hash: 2ede9dd24b586f538c900966944bc0f2886a92f2016417db33660dbcb87d2aba",
    "postEndpoint": "https://shadow-storage.genesysgo.net/upload",
    "fileNamesHashed": "2ede9dd24b586f538c900966944bc0f2886a92f2016417db33660dbcb87d2aba"
}
```

The result of the upload is always:

POST https://shadow-storage.genesysgo.net/upload 401 (Unauthorized)

## To Reproduce
### Create a new Keypair and Shdw storage account

```bash
solana-keygen new -o test.json
solana address --keypair test.json
```

Give it some $SOL and $SHDW.

Create a SHDW storage account and note the address.

### Setup `.env`

Create `.env`
```bash
cp .env.example .env 
```

Grab your secret key
```bash
cat test.json
```

Fill out the storage account and private key within `.env`

### Run

Now install and run the app.

```bash
bun install
bun dev
```

Go to `http://localhost:3000`

Upload a file and press `Submit`

## Environment

```bash
bun --version
1.0.0
```

