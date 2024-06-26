# intermediate-1
Solidity Smart Contract with Error Handling:-
This repository contains a simple Solidity smart contract demonstrating the use of require(), assert(), and revert() statements for error handling.


*require: Used to enforce conditions that must be met for a function to execute.

*assert: Used to assert conditions that should always be true. If false, it indicates an internal error.

*revert: Used to revert execution and provide an error message.
These mechanisms are crucial for ensuring the correctness and safety of smart contracts running on the Ethereum blockchain, helping to prevent unintended behavior and potential security vulnerabilities.

Smart Contract
The smart contract, ErrorHandling, includes three functions:

*addToBalance(uint256 amount): Adds the specified amount to the contract's balance. It uses require() to ensure the amount is greater than zero.

*checkBalance(): Checks that the balance is non-negative using assert(). This is for demonstration purposes.

*withdraw(uint256 amount): Withdraws the specified amount from the contract's balance. It uses revert() to handle cases where the amount exceeds the balance

EXECUTING PROGRAM :-

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.


code:-


     // SPDX-License-Identifier: MIT
     pragma solidity ^0.8.0;

     contract ErrorHandling {
    uint256 public balance;

    // Function to add to balance using require()
    function addToBalance(uint256 amount) public {
        require(amount > 0, "Amount must be greater than zero");
        balance += amount;
    }

    // Function to check balance using assert()
    function checkBalance() public view {
        // This assert will always be true, for demonstration purposes
        assert(balance >= 0);
    }

    // Function to withdraw from balance using revert()
    function withdraw(uint256 amount) public {
        if (amount > balance) {
            revert("Insufficient balance");
        }
        balance -= amount;
    }
       }


    function checkBalance() public view returns (uint) {
        return accountBalances[msg.sender];
    }
     }


