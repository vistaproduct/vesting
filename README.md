# Token Vesting Smart Contract

This repository contains a Solidity smart contract that implements a **token vesting** mechanism. It allows tokens to be distributed to beneficiaries over a specified period of time.

## Features

- ⏳ **Vesting Schedule**: Tokens are unlocked gradually over a specified duration.
- 👥 **Multiple Beneficiaries**: The contract owner can add multiple beneficiaries with specific token allocations.
- 🎁 **Claim Tokens**: Beneficiaries can claim their vested tokens as they become available.
- 🔐 **Security**: The contract ensures that tokens can only be claimed based on the vesting schedule.

## Contract Details

- **Token**: ERC20 compatible token (passed during contract deployment).
- **Vesting Duration**: The period over which tokens are vested, set during contract deployment.
- **Start Time**: Vesting begins when the contract is deployed.
- **Beneficiaries**: Each beneficiary has a specific token allocation and can claim tokens progressively.

## Functions

### `addBeneficiary(address beneficiary, uint256 amount)`
- Adds a new beneficiary with a specified number of tokens to be vested.
- Only callable by the owner.

### `claimTokens()`
- Allows a beneficiary to claim the tokens they are entitled to at the current moment based on the vesting schedule.

### `remainingTokens(address beneficiary)`
- Returns the remaining tokens that the beneficiary has yet to claim.

## How to Use

1. Deploy the contract with an ERC20 token address and a vesting duration (in seconds).
2. Use `addBeneficiary` to allocate tokens to each beneficiary.
3. Beneficiaries can call `claimTokens` to withdraw the amount of tokens available to them based on the vesting schedule.

## Example

```solidity
IERC20 token = IERC20(0xYourTokenAddress);
TokenVesting vestingContract = new TokenVesting(token, 365 days);
vestingContract.addBeneficiary(0xBeneficiaryAddress, 1000 * 10**18);
