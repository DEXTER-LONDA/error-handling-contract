# Error Handling Contract

This Solidity program is a simple "errorHandlingContract" program that demonstrates the basic syntax and functionality of the Solidity programming language. The purpose of this program is to implement require(), assert(), and revert() statement.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. This is a contract that implement the require(), assert(), and revert() statements.

this contract contain public variable called "value" and two functions "setValue" and performDivision".

"setValue" function contain one argument "_value" and there is require() statement which is used to check the condition that input "_value" is greater than "zero". If not it will show statement "Value must be greater than 0.". Then value of "_value" is kept in "previousValue" for later comparision. then value of "value" is being updated with the value of "_value". There is assert() statement which check that the value of "_value" has been successfully assigned to "value" or not if not it will retrive the value, if yes then it will assure that current value is not equal to previousvalue if they are equal then it will retrive the value.

"performDivision" function takes two arguments "_num" and "_denom" which are numerator and denomenator respectivly. In this function require() statement check the condition that "_denom" is not equal to zero if this condition fails then it will show a statement "Cannot divide by zero.". If this condition is passed with success, there is a "if" statement with condition that if "_num" is divided by "_dnom" it will give remender and it is not equal to "zero". If this condition pass it will "revert" the staement "Numerator is not fully divisible by denominator.", if it will fail it give the result of "_num" divided by "_denom".

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., ErrorHandlingContract.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT 
pragma solidity ^0.8.1;

contract ErrorHandlingContract {
    uint public value;

    function setValue(uint _value) public {  
        require(_value > 0, "Value must be greater than 0.");
        uint256 previousValue = value;
        value = _value;
        assert(value == _value);
        assert(value != previousValue);
   }

    function performDivison(uint _num, uint _denom) public pure returns (uint) { 
      require(_denom != 0, "Cannot divide by zero.");
      if (_num % _denom != 0) {
        revert("Numerator is not fully divisible by denominator.");
      }
      return _num / _denom;
   }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.1", and then click on the "Compile ErrorHandlingContract.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "ErrorHandlingContract" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the sayHello function. Click on the "HelloWorld" contract in the left-hand sidebar, and then enter the value in the "setValue" function. Finally, click on the "transact" button to execute the function and then call "value" to check the current value.

give the values of numerator to "_num" and denomenator to "_denom" then click on the "transact" button it will show the answer of division.

