# ETH_Token

This program is written on Solidity and has very basic functionalities related to the creation of Tokens.

## Description

This program consists of simple functions and variables which helps in mapping of the data along with its minting and also helps us to burn the resources whenever needed.
## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.7;

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

    string public TokenName ;
    string public TokenAbbrv ;
    uint public TotalSupply ;

    //Constructor to initialise values

    constructor(string memory _TokenName, string memory _TokenAbbrv)
    {
           TokenName = _TokenName;
           TokenAbbrv = _TokenAbbrv;
           TotalSupply = 0;
    }

    // mapping variable here

    mapping (address => uint) public balances;

    // mint function

    function mint(address _address, uint _value) public 
    {
       require(_address != address(0), "The Entered Address is not Valid");
       require(_value > 0, "0 resources cannot be minted");
       TotalSupply += _value;
       balances[_address] += _value;
    }

    // burn function
     function burn(address _address, uint _value) public 
    {
        require(_address != address(0), "The Entered address is not Valid");
        require(_value > 0, "0 number of resources cannot be burned");
        require(balances[_address] >= _value,"There is not enough resources to burn");
        
        TotalSupply -= _value;
        balances[_address] -= _value;
        
    }

}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.7" (or another compatible version), and then click on the "Compile myToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "HelloWorld" contract from the dropdown menu, and then click on the "Deploy" button.

Now inorder for the Deployment to work we have to enter the TokenName and TokenAbbreviation beforehand. Then the project will be deployed after which we can select any address(by default we can select the address of the account by clicking on the copy icon at tht top of the screen). Then when we enter the values for minting it checks for valid values and displays output for the invalid ones. The same is true for the burn function.

## Authors

Akhanda Pal Biswas
[@Chandigarh University](https://www.linkedin.com/in/akhanda-pal-biswas-445a88230/)


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
