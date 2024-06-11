# Error Handling Contract

This Solidity program is a simple "errorHandlingContract" program that demonstrates the basic syntax and functionality of the Solidity programming language. The purpose of this program is to implement require(), assert(), and revert() statement.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. This is a contract that implement the require(), assert(), and revert() statements.

This contract contain public variable called "totalBalance" and four functions "deposit", "withdraw", "transfer", and "cancelTransaction".

First we have done ther mapping of account and the balances.

"deposit" function helps us to deposit the ether into the contract. In this function the require() statement is used to check the condition that value is greater than zero, if not it show the statement "Deposit amount must be greater than zero." and if condition pass it will increment the balance by the value and update total balance by the value.

"withdraw" function helps us to withdraw the ether from the contract. This contract takes one argument that is amount. In this function require() ataement is used to check the condition thatr the amout to be withdraw should be less than the balance of the account, if not it will show the statement "Insufficient balance." and if yes then it will proceed and put current balance in the previousBalance for further comparision. it will decrement the balance by the amount and it will update the totalBalance. In this assert() atatement is used assure that the current balance is less than the previousBalance.

"transfer" function helps us to transfer the ether within the contract. This function takes two argument that are address as "to" and amount. In this function require() statement is used two times first to check that the provided address is not equal to zero is this condition if false then it will show statement "Invalid address." and if it is true than next statement check the condition that the amount to be tranfered is less than the current balance, if not it will show statement "Insufficient balance." if yes it will decrement the balance and update the balance by the amount.

"cancelTransaction" function that revert is some condition is not met. In this function we set someCondition to false and apply if statemnt with the condition opposite of someCondition that is true and inside if statement we have used revert() statement which revert the statement "Transaction cancelled due to some condition.".

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., ErrorHandlingContract.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract ErrorHandlingContract {
    uint256 public totalBalance;
    mapping(address => uint256) public balances;

    function deposit() public payable {
        require(msg.value > 0, "Deposit amount must be greater than zero.");
        balances[msg.sender] += msg.value;
        totalBalance += msg.value;
    }

    function withdraw(uint256 amount) public {
        require(amount <= balances[msg.sender], "Insufficient balance.");
        
        uint256 previousBalance = balances[msg.sender];
        balances[msg.sender] -= amount;
        totalBalance -= amount;
        
        assert(balances[msg.sender] <= previousBalance);
    }

    function transfer(address to, uint256 amount) public {
        require(to != address(0), "Invalid address.");
        require(amount <= balances[msg.sender], "Insufficient balance.");
        
        balances[msg.sender] -= amount;
        balances[to] += amount;
    }

    function cancelTransaction() public pure {
        bool someCondition = false;

        if (!someCondition) {
            revert("Transaction cancelled due to some condition.");
        }
    }
}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18", and then click on the "Compile ErrorHandlingContract.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "ErrorHandlingContract" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it. Click on the "ErrorHandlingContract" contract in the left-hand sidebar, and then click on deposit button to depositb the amount. And enter the address in the balavce section to check the balance of the account. to transfer the ether enter the address and the amount to be transfered. To withdraw the ether enter the amount of the ether to be withdraw.


