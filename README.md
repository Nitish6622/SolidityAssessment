# MyToken Contract

The MyToken contract is a simple ERC-20-like token implementation in Solidity. It includes basic functionalities for minting and burning tokens. The contract is designed to manage a token with a name, abbreviation, and total supply. 

## Description

The mint and burn functions are public, meaning they can be called by anyone. In a real-world scenario, these functions should be restricted to specific roles (e.g., only the owner or authorized addresses can mint or burn tokens).
The require statement in the burn function ensures that tokens cannot be burned from an address with insufficient balance, preventing unintended negative balances.

## Getting Started

### Installing

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

### Executing program

To execute and interact with this Solidity contract, you'll need to use a development environment that supports Ethereum smart contracts. One of the most popular tools for this purpose is Remix, an online Solidity IDE. Here’s a step-by-step guide on how to deploy and test the contract using Remix:
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile MyToken.sol" button.

Open Remix and Go to Remix IDE.Create a New File:
In the file explorer on the left, click the "New File" button.
Name your file MyToken.sol.
then Compile the Contract:
Click on the "Solidity Compiler" tab (the one with a little "S" icon on the left sidebar).
Ensure the compiler version is set to 0.8.18 (or a compatible version).
Click the "Compile MyToken.sol" button.
Deploy the Contract:
Go to the "Deploy & Run Transactions" tab (the one with the Ethereum logo on the left sidebar).
Select the environment (e.g., "JavaScript VM" for a local blockchain simulation).
Make sure the contract MyToken is selected in the contract dropdown.
Click the "Deploy" button.
Once deployed, the contract will appear in the "Deployed Contracts" section.
Expand the deployed contract to see the available functions.
```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
string public tokenName = "Nitish";
string public tokenAbb = "Nti";
uint public totalUnitSupply =0;


    // mapping variable here
    mapping(address => uint) public balance;

    // mint function
    function mint (address _address, uint _value) public {
      totalUnitSupply += _value;
      balance[_address] += _value;
    }

    // burn function
function burn (address _address, uint _value) public {
  if(balance[_address] >= _value) {
      totalUnitSupply -= _value;
      balance[_address] -= _value;
}
}
}
```

## Help

When working with Solidity contracts, common problems include compiler errors, gas limit issues, and unauthorized access to critical functions. To address these, ensure you're using the correct compiler version and syntax, allocate sufficient gas for transactions, and implement access control mechanisms like OpenZeppelin's Ownable contract to restrict sensitive operations such as minting and burning tokens to authorized addresses only. 
```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is Ownable {
    // Public variables to store token details
    string public tokenName = "Nitish";
    string public tokenAbbrv = "Nti";
    uint public totalSupply = 0;

    // Mapping to store balances of addresses
    mapping(address => uint) public balances;

    // Mint function to increase total supply and balance of an address
    function mint(address _address, uint _value) public onlyOwner {
        totalSupply += _
```

## Authors

Contributors names and contact info

Nitish 
@lavis5599@gmail.com


## License

This project is licensed under the  MIT  License - see the LICENSE.md file for details
