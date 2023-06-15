# IbroToken.sol

This Smart Contract shows the functionalities to create, mint and burn tokens.

## Description

This smart contract contains three public variables (tokeName, tokenAbbrv and totalSupply) that hold the details of the Ibro coin, a mapping of addresses to balances (address => uint), a mint function used to mint tokens, this take two parameters (address, value) and a burn function which also takes two same parameters and is used to destroy tokens.

The burn function has a conditionals to make sure the balance of "sender" is greater than or equal to the amount that is supposed to be burned.

## Getting Started

### Executing program

You can execute this on your local environment or use Remix IDE (Recommended) => https://remix.ethereum.org/.

For Remix IDE, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g. IbroToken.sol). Copy and paste the following code into the file:

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

contract IbroToken {

    // public variables here
    string public tokenName = "Ibro";
    string public tokenAbbrv = "IB";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }
    // burn function
    function burn(address _address, uint _value) public {
        if(balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}


```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to to a compatible solidity version, and then click on the "Compile IbroToken.sol" button.

You can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select "IbroToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once deployed, you can interact with it by calling and passing the appropriate arguements the mint and burn functions.

## Authors

Chris Surulere

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
