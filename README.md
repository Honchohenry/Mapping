# Mapping

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;
contract Mapping{
    mapping(uint => bool) public myMapping;
    mapping(address => bool) public myAddressMapping;
    mapping(uint => mapping(uint =>bool)) public uintBoolMapping;

    function setValue(uint _index) public {
        myMapping[_index] = true;
    }

    function setMyAddressToTrue() public {
        myAddressMapping[msg.sender] = true;
    }

    function setUintMapping(uint _key1, uint _key2, bool _value) public {
        uintBoolMapping[_key1][_key2]= _value;
    }
}
# Mapping Withdrawals
contract MappingWithdrawals{

    mapping(address => uint) public balanceReceived;


    function sendMoney() public payable{
        balanceReceived[msg.sender] += msg.value;
    }

    function getBalance() public view returns(uint) {
        return address(this).balance;
    }

    function withdrawallMoney(address payable _to) public {
          uint balanceToSendOut = balanceReceived[msg.sender];
          balanceReceived[msg.sender] = 0;
         _to.transfer(balanceToSendOut); 
    }
}


