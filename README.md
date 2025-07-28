# 🔐 VaultSystemProject

## 💡 Overview
This project demonstrates the development and auditing of Ethereum smart contracts involving a simple Vault system and a vulnerable PiggyBank. It includes contracts for secure deposit and withdrawal of Ether, simulation of exploits, and application of inheritance and modular design principles.

---

## 📁 Contracts Included

| Contract             | Purpose                                             |
|---------------------|-----------------------------------------------------|
| `VaultBase.sol`     | Abstract base contract for structure and state      |
| `VaultManager.sol`  | Inherits from `VaultBase` and handles core logic    |
| `VulnerablePiggyBank.sol` | Example of insecure contract to be audited   |
| `SecurePiggyBank.sol`     | Improved version with access controls       |
| `Attacker.sol`      | Contract used to simulate exploit on vulnerable bank|

---

## 🔍 Vulnerabilities Identified

- ❌ **Unrestricted Withdrawals**: Anyone could call `withdraw()` and drain contract funds
- ❌ **No Access Control**: Withdrawals were not limited to the contract owner
- ❌ **Poor Input Validation**: Deposit function allowed sending 0 ETH

---

## ✅ Security Fixes

- ✅ `require(msg.sender == owner)` to restrict withdrawals
- ✅ Rejected zero-value deposits using `require(msg.value > 0)`
- ✅ Added `Deposit` and `Withdraw` events for logging
- ✅ Restructured contracts using inheritance (`VaultBase → VaultManager`)

---

## 💣 Attack Simulation

The `Attacker` contract:
- Receives the address of a deployed `VulnerablePiggyBank`
- Calls `withdraw()` to exploit lack of access control
- ETH is transferred to the attacker's wallet via `receive()` fallback

---

## 🧪 Tools Used

- [Remix IDE](https://remix.ethereum.org) for coding, compiling, and deploying
- MetaMask wallet & Injected Provider (used during testing)
- GitHub for version control and documentation

---

## 🧑🏽‍💻 Author

**Najibat**  
Smart Contract Developer  
Location: Abuja, Nigeria  
Date: July 2025

---

## 📌 How to Use

1. Open Remix IDE
2. Paste and compile the contracts
3. Deploy using JavaScript VM or Injected Provider
4. Deposit ETH → Test withdrawal → Simulate attack → Fix & retest

---

Feel free to fork or contribute to expand the system with features like:
- Multi-sig access control
- Time-locked withdrawals
- ERC-20 support

