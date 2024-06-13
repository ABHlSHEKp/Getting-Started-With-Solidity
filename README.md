# Getting-Started-With-Solidity


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
