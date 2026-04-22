# CryptoBank Smart Contract

A secure and minimal multi-user Ethereum bank smart contract built in Solidity.

## Overview

CryptoBank is a smart contract that allows multiple users to deposit and withdraw Ether while enforcing strict security and balance constraints. The contract ensures that users can only withdraw their own funds and prevents exceeding a configurable maximum balance.

This project demonstrates fundamental smart contract design patterns such as access control, secure Ether transfers, and state management.

---

## Features

* Multi-user support
* Secure Ether deposits
* Controlled withdrawals
* Per-user balance tracking
* Maximum balance limit enforcement
* Admin-controlled configuration

---

## Contract Architecture

### State Variables

* `maxBalance`: Maximum Ether allowed per user
* `admin`: Contract owner with special permissions
* `userBalance`: Mapping storing each user's balance

---

### Core Functions

#### 1. depositEther()

Allows users to deposit Ether into the contract.

* Updates user balance
* Enforces maximum balance limit
* Emits deposit event

---

#### 2. withdrawEther(uint256 amount)

Allows users to withdraw their deposited Ether.

* Checks sufficient balance
* Updates state before transfer (security best practice)
* Transfers Ether using low-level call
* Emits withdraw event

---

#### 3. modifyMaxBalance(uint256 newMaxBalance)

Admin-only function to update the maximum allowed balance.

---

## Security Considerations

* Checks-Effects-Interactions pattern used in withdrawals
* Access control via `onlyAdmin` modifier
* Prevents balance overflow beyond limit
* Reverts on failed Ether transfers

---

## Example Scenario

1. User A deposits 5 ETH
2. User B deposits 2 ETH
3. User A withdraws 2 ETH
4. User A deposits again within limit

---

## Tech Stack

* Solidity ^0.8.30
* Ethereum Virtual Machine (EVM)

---

## Author

Cristian Tudela
Blockchain Developer
