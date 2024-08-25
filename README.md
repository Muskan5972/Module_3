# Module_3
## Project Title  
DegenToken ERC20 Contract with Loyalty Points

## Problem Statement
Create an ERC20 token named DegenToken with built-in functionality for loyalty points, allowing token holders to earn additional tokens based on the duration they hold the tokens. The contract should also include minting, transferring, burning,checking balance and redeeming tokens features.

## Prerequisites
Solidity ^0.8.18

OpenZeppelin Contracts v4.4.0 

## Description  
The DegenToken contract is an ERC20 token implementation with the following features:

1. Loyalty Points: Users earn loyalty points based on the duration they hold the tokens.
2. Minting: The owner can mint new tokens.
3. Transferring: Tokens can be transferred between users.
4. Burning: Users can burn their tokens.
5. Redeeming: Users can redeem tokens for specific items.
6. Check Balance: Checks token Balance of Caller.


## Getting Started

### Installing  
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension. Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    constructor(string memory tokenName, string memory symbol)
        ERC20(tokenName, symbol)
            Ownable(msg.sender) // Pass the owner address to Ownable constructor
    {}

    // Mint tokens
    function mintToken(address _sendto, uint256 _amount) public onlyOwner {
        require(_sendto != address(0), "Cannot mint to the zero address");
        require(_amount > 0, "Amount should be greater than zero");
        _mint(_sendto, _amount);
    }

    // Burn tokens
    function burnToken(uint256 _amount) public {
        require(_amount > 0, "Amount to burn should be greater than zero");
        require(balanceOf(msg.sender) >= _amount, "Insufficient balance to burn");
        _burn(msg.sender, _amount);
    }

    // Transfer tokens
    function transferToken(address _toanother, uint256 _amounttransfer) public returns (bool) {
        require(_toanother != address(0), "Cannot transfer to the zero address");
        require(_amounttransfer > 0, "Amount should be greater than zero");
        return super.transfer(_toanother, _amounttransfer);
    }
}


```

###  Executing program    
#### How to Run the Program      
1. Install the necessary dependencies using the following command:
npm install @openzeppelin/contracts
2. Compile the Solidity contract.
3. Deploy the contract using your preferred Ethereum development environment.  

#### For Remix:    
1. Open Remix IDE.  
2. Upload Game.sol.  
3. Compile and deploy the contract.  


## Authors  
Muskan @Muskan5972

## License  
This project is licensed under the MIT License - see the LICENSE.md file for details.  

We have established a solidity contract with this code. 
