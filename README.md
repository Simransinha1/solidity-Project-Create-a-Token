Project: Create a Token

Description
This Solidity smart contract project aims to create a simple ERC20 token, allowing developers to deploy their own custom tokens on the Ethereum blockchain. The ERC20 standard is widely used for creating fungible tokens, meaning each token is identical and interchangeable with others of the same value.

This token contract will implement the basic functionalities of an ERC20 token, including minting new tokens and burning existing ones. It will store essential token details like token name, token abbreviation, and total supply, and maintain a mapping of addresses to token balances.

Getting Started

Prerequisites
To work with this project, you'll need:

1. A development environment for Solidity contracts (e.g., Remix, Hardhat, Truffle).
2. Basic knowledge of the Ethereum blockchain and smart contracts.
3. An Ethereum wallet to interact with the contract (e.g., MetaMask).

Installing
1. Create a new Solidity file (e.g., `MyToken.sol`) in your preferred development environment.
2. Copy and paste the contract code from the provided source code.
3. Save the file in the root folder of your project.

Executing Program
1. Deploy the contract to an Ethereum development network of your choice (e.g., Rinkeby, Ropsten) using your development environment.
2. Interact with the deployed contract through a web-based IDE (e.g., Remix) or your custom frontend application.
3. To mint new tokens, call the `mint` function, passing the recipient's address and the number of tokens to create.
4. To burn existing tokens, call the `burn` function, specifying the address to burn tokens from and the amount to be burned.
5. Ensure that the balance of the sender is sufficient before calling the `burn` function.

Example Usage:
```
pragma solidity 0.8.18;

contract MyToken {
    string public name = "My Token";
    string public symbol = "MT";
    uint256 public totalSupply;

    mapping(address => uint256) public balances;

    constructor(uint256 _initialSupply) {
        totalSupply = _initialSupply;
        balances[msg.sender] = _initialSupply;
    }

    function mint(address account, uint256 value) public {
        require(account != address(0), "Invalid address");
        totalSupply += value;
        balances[account] += value;
    }

    function burn(address account, uint256 value) public {
        require(account != address(0), "Invalid address");
        require(balances[account] >= value, "Insufficient balance");
        totalSupply -= value;
        balances[account] -= value;
    }
}
```
