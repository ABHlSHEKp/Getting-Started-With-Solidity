# Create a token
We will create our very own token! Well, not really, but kinda! Either way, it’s going to be a lot of fun, so let’s get to the deetz!

## Description

Our contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
Our contract will have a mapping of addresses to balances (address => uint)
We will have a mint function that takes two parameters: an address and a value. The function then increases the total supply by that number and increases the balance of the address by that amount.
Our contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. It will take an address and value just like the mint functions. It will then deduct the value from the total supply and from the balance of the address.
Lastly, our burn function should have conditionals to make sure the balance of account is greater than or equal to the amount that is supposed to be burned.

## Getting Started

### Installing

* Use REMIX IDE for the code running platform.

### Executing program

* How to run the program
* Step-by-step bullets
```
// SPDX-License-Identifier: MIT
pragma solidity >=0.6.12 <0.9.0;


import "@openzeppelin/contracts/utils/math/SafeMath.sol";

contract MyToken {
    using SafeMath for uint;

    string public tokenName = "Abhi";
    string public tokenAbbrv = "A";
    uint public totalSupply = 0;

    mapping(address => uint) public balances;

   
    event Mint(address indexed to, uint value);

   
    event Burn(address indexed from, uint value);

    function mint(address _address, uint _value) public {
        totalSupply = totalSupply.add(_value);
        balances[_address] = balances[_address].add(_value);
        emit Mint(_address, _value);
    }

    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance");
        totalSupply = totalSupply.sub(_value);
        balances[_address] = balances[_address].sub(_value);
        emit Burn(_address, _value);
    }
}
```

## Help

Any advise for common problems or issues.
```
Watching provided video would be enough for well understanding of this project.
```

## Authors

Contributors names and contact info

Abhishek Pathak
Email: pathakabhishek773@gmail.com


## License

This project is licensed under the [ABHISHEK] License - see the LICENSE.md file for details
