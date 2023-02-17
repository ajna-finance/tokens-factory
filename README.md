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