# Test Token Factory
This repository provides a factory for minting tokens for testing purposes.
The factory can be used to create:
- ERC20 tokens with configurable number of decimal places.
- ERC721 and ERC1155 NFTs.

The EOA which created the token becomes the owner, and has the ability to mint.

## Deployment Using Foundry
```
make deploy
```

## Usage

First, set `TOKENSFACTORY` environment to the address of the deployed factory.

As an example, to create an 18-decimal ERC20 token:
```
cast send ${TOKENSFACTORY} "createERC20Token(string,string,uint8)" \
    "Test Token" "TEST" 18 \
    --from ${DEPLOY_ADDRESS} --keystore ${DEPLOY_KEYSTORE}
```

Look at logs emitted from the transaction to determine the new token contract address, and export to your environment as `TOKEN_ADDRESS`.  Then run the following to mint one million tokens, substituting the addess to receive minted funds:

```
cast send ${TOKEN_ADDRESS} "mint(address,uint256)" <mint_to_address> 1000000ether \
    --from ${DEPLOY_ADDRESS} --keystore ${DEPLOY_KEYSTORE}
```

On public testnets, the owner may use the Etherscan UI to mint tokens.  To do so, navigate to the tokens factory contract address, choose _Contract_, and then _Write Contract_.  Connect your wallet, click one of the token types, provide parameters, click _Write_, and sign the transaction with your wallet.
