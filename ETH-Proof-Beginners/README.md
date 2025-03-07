# MyToken

This Solidity program is a basic implementation of a token contract, demonstrating the fundamental concepts of creating and managing a custom cryptocurrency token on the Ethereum blockchain. The contract includes basic functionalities for minting and burning tokens, making it a useful starting point for those interested in understanding how tokens work within smart contracts.

## Description

The MyToken contract is a simple ERC20-like token written in Solidity, designed for educational purposes. It includes essential features such as minting new tokens and burning existing ones. The contract also tracks the total supply of tokens and the balances of individual addresses.

## Getting Started

### Executing the Program

To interact with this contract, users can use Remix, an online Solidity IDE. Follow these steps to get started:

1. *Access Remix IDE:*
   - Visit the Remix website at [https://remix.ethereum.org/](https://remix.ethereum.org/).

2. *Create a New File:*
   - In the left-hand sidebar, click on the "+" icon to create a new file.
   - Save the file with a .sol extension (e.g., MyToken.sol).

3. *Add the Contract Code:*
   - Copy and paste the following code into the new file:

     solidity
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

    // Public variables here
    string public tokenName = "artifacts"; 
    string public tokenAbbrv = unicode"ΜΤΑ";
    uint public totalSupply = 0;

    // Mapping variable here
    mapping(address => uint) public balances;

    // Mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Burn function
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
    
}
     

4. *Compile the Code:*
   - Click on the "Solidity Compiler" tab in the left-hand sidebar.
   - Ensure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" button.

5. *Deploy the Contract:*
   - Click on the "Deploy & Run Transactions" tab in the left-hand sidebar.
   - Select the "MyToken" contract from the dropdown menu.
   - Click on the "Deploy" button.

6. *Interact with the Contract:*
   - After deployment, interact with the contract by calling the mintTokens and burnTokens functions.
   - To mint tokens, enter the address and amount, and click "transact."
   - To burn tokens, similarly enter the address and amount, and click "transact."

## Authors

Sachin Verma
[LinkedIn](www.linkedin.com/in/sachin-verma-444790188/)

## License

This project is licensed under the MIT License - see the LICENSE.txt file for details.
