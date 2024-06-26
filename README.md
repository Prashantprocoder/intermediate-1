# intermediate-1
Solidity Smart Contract with Error Handling:-
This repository contains a simple Solidity smart contract demonstrating the use of require(), assert(), and revert() statements for error handling.

Smart Contract
The smart contract, ErrorHandling, includes three functions:

*addToBalance(uint256 amount): Adds the specified amount to the contract's balance. It uses require() to ensure the amount is greater than zero.

*checkBalance(): Checks that the balance is non-negative using assert(). This is for demonstration purposes.

*withdraw(uint256 amount): Withdraws the specified amount from the contract's balance. It uses revert() to handle cases where the amount exceeds the balance



code:-



      // SPDX-License-Identifier: MIT
        pragma solidity ^0.8.20;

     contract SimpleBank {
         address public admin;
    mapping(address => uint) private accountBalances;

    modifier onlyAdmin() {
        require(msg.sender == admin, "Unauthorized: Only admin can execute this");
        _;
    }

    constructor() {
        admin = msg.sender;
    }

    event FundsDeposited(address indexed user, uint amount);
    event FundsWithdrawn(address indexed user, uint amount);

    function addFunds() public payable {
        require(msg.value > 0, "Deposit must be greater than zero");
        accountBalances[msg.sender] += msg.value;
        emit FundsDeposited(msg.sender, msg.value);
    }

    function withdrawFunds(uint amount) public {
        require(amount > 0, "Withdrawal amount must be greater than zero");
        require(accountBalances[msg.sender] >= amount, "Insufficient balance");

        uint initialContractBalance = address(this).balance;
        require(initialContractBalance >= amount, "Contract balance is low");

        accountBalances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
        require(address(this).balance == initialContractBalance - amount, "Balance mismatch after withdrawal");

        emit FundsWithdrawn(msg.sender, amount);
    }

    function checkBalance() public view returns (uint) {
        return accountBalances[msg.sender];
    }
     }


