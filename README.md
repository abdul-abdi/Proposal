# BLOCKCHAIN PROPOSAL MANAGEMENT SYSTEM

# Introduction
This smart contract allows users to create proposals, vote on them, and manage their lifecycle. It's designed to be used on the Internet Computer platform, leveraging the IC SDK and Rust programming language.

# Contract Overview
Memory Management
The contract uses a virtual memory manager to handle data storage efficiently. It employs stable data structures provided by ic_stable_structures.

# Proposal Structure
Proposals are represented by the Proposal struct, containing information such as description, approval, rejection, pass counts, and voter details.

# Error Handling
The contract defines custom error types (VoteError) to handle various scenarios, such as attempting to vote multiple times, modifying a non-existent proposal, or unauthorized access.

# Functions
get_proposal(key: u64) -> Option<Proposal>
Retrieves a proposal by its unique identifier.

get_proposal_count() -> u64
Returns the total count of proposals.

create_proposal(key: u64, proposal: CreateProposal) -> Option<Proposal>
Creates a new proposal with the specified details.

edit_proposal(key: u64, proposal: CreateProposal) -> Result<(), VoteError>
Edits an existing proposal, given the correct permissions.

end_proposal(key: u64) -> Result<(), VoteError>
Ends an active proposal, preventing further votes.

vote(key: u64, choice: Choice) -> Result<(), VoteError>
Allows a user to cast their vote on a specific proposal.

# Getting Started

To get started, you might want to explore the project directory structure and the default configuration file. Working with this project in your development environment will not affect any production deployment or identity tokens.

To learn more before you start working with Proposal, see the following documentation available online:

- [Quick Start](https://internetcomputer.org/docs/current/developer-docs/setup/deploy-locally)
- [SDK Developer Tools](https://internetcomputer.org/docs/current/developer-docs/setup/install)
- [Rust Canister Development Guide](https://internetcomputer.org/docs/current/developer-docs/backend/rust/)
- [ic-cdk](https://docs.rs/ic-cdk)
- [ic-cdk-macros](https://docs.rs/ic-cdk-macros)
- [Candid Introduction](https://internetcomputer.org/docs/current/developer-docs/backend/candid/)

If you want to start working on your project right away, you might want to try the following commands:

```bash
cd Proposal/
dfx help
dfx canister --help
```

## Running the project locally

If you want to test your project locally, you can use the following commands:

```bash
# Starts the replica, running in the background
dfx start --background

# Deploys your canisters to the replica and generates your candid interface
dfx deploy
```

Once the job completes, your application will be available at `http://localhost:4943?canisterId={asset_canister_id}`.

If you have made changes to your backend canister, you can generate a new candid interface with

```bash
npm run generate
```

at any time. This is recommended before starting the frontend development server, and will be run automatically any time you run `dfx deploy`.

If you are making frontend changes, you can start a development server with

```bash
npm start
```

Which will start a server at `http://localhost:8080`, proxying API requests to the replica at port 4943.


# This is the idea behind the smart contract, due to time constraints we could not implement all the functionalities:

Welcome to our cutting-edge decentralized lending platform, where transparency, security, and efficiency converge through the power of a robust and secure smart contract operating on Ethereum Virtual Machine (EVM) compatible networks. This platform is designed to revolutionize lending and borrowing processes, seamlessly connecting borrowers and lenders while prioritizing security, gas optimization, simplicity, risk management, and collateral management.

# Section 1: Loan Creation
# Part 1.1: Borrower Initiates Loan Request
User Input:
Borrowers kick off the loan creation process by furnishing personal details, including legal name, address, and KYC information. Simultaneously, borrowers define loan parameters such as the desired amount, proposed interest rate, repayment terms, and the type of collateral.

KYC Verification:
Thorough KYC verification is conducted by the smart contract to ensure the borrower's identity. Secure key management safeguards sensitive KYC data. This process involves validating identification documents, regulatory compliance checks, and confirming the borrower's eligibility.

Collateral Validation:
The smart contract verifies the authenticity and eligibility of the provided collateral, maintaining the platform's standards and security.

# Part 1.2: Smart Contract Verification
Risk Management Criteria:
A comprehensive set of risk management criteria evaluates the loan request, assessing creditworthiness, debt-to-income ratios, and historical repayment behavior to align with the platform's risk tolerance.

Loan Approval Process:
Upon successful verification, the smart contract approves the loan request, generating a unique identifier and creating a transparent and immutable loan asset on the blockchain.

Metadata Storage:
Detailed loan terms, including repayment schedules and collateral information, are securely stored in the asset's metadata for easy access, transparency, and compliance.

Security and Gas Optimization Enhancements:
Rigorous security audits, multi-signature approval, gas optimization techniques, access controls, and encryption are implemented to fortify the smart contract.

# Section 2: Loan Investment
# Part 2.1: Lender Participation
Loan Asset Information:
Lenders access comprehensive information about available loan assets, borrower profiles, risk metrics, and historical performance data, enabling informed investment decisions.

Platform Investment Limits:
Smart contracts verify that proposed investments adhere to platform-specific limits, ensuring fair and balanced distribution among lenders.

# Part 2.2: Investment Process
Funds Transfer:
Lenders initiate the investment process by transferring funds in supported cryptocurrency, prioritizing gas optimization to minimize transaction costs.

Investment Limits Check:
The smart contract rigorously checks proposed investment amounts against predefined limits to prevent excessive investments and maintain platform stability.

# Part 2.3: Loan Token Minting
Token Generation:
Upon successful transfer, the smart contract mints loan tokens for lenders, ensuring fair and transparent ownership distribution.

Token Deposit:
Minted loan tokens are deposited directly into the lender's wallet, simplifying tracking and enabling easy withdrawal or trading.

Security and Gas Optimization Enhancements:
Secure fund transfer channels, gas optimization, and rate-limiting mechanisms are integrated for secure and efficient transactions.

# Section 3: Loan Repayment
# Part 3.1: Borrower Repayment
Repayment Schedule:
Borrowers adhere to a predefined repayment schedule, automating the deduction of repayments from their wallet to minimize the risk of missed payments.

# Part 3.2: Distribution of Repayments
Accurate Calculation:
Precise algorithms calculate repayment amounts, ensuring fair distribution among lenders by considering interest, outstanding principal, and additional fees.

Real-time Updates:
Lenders receive real-time updates on accrued interest and remaining repayments, fostering transparency and trust.

# Part 3.3: Withdrawal Option
Withdrawal Request:
Lenders can initiate withdrawal requests at any time, allowing flexibility in managing funds based on market conditions or personal preferences.

Flexible Withdrawal:
Withdrawal requests are processed promptly, transferring cryptocurrency directly to the lender's wallet for maximum flexibility.

Security and Gas Optimization Enhancements:
Secure channels for automated repayments, gas optimization, and event-driven mechanisms for real-time updates enhance security and reduce transaction costs.

# Section 4: Collateral Management
# Part 4.1: Collateral Storage
Decentralized Vault:
Borrower collateral is securely stored in a decentralized vault, managed by the smart contract, mitigating the risk of a single point of failure.

# Part 4.2: Value Monitoring
Real-time Monitoring:
Continuous real-time monitoring of collateral market value ensures accurate and up-to-date valuation through decentralized oracles.

Automated Alerts:
Automated alerts are generated when the collateral's value approaches predefined thresholds, serving as an early warning system.

# Part 4.3: Liquidation Trigger
Threshold Evaluation:
Regular evaluation against predefined thresholds triggers the collateral liquidation process to protect lenders' interests.

Market Value Liquidation:
During liquidation, the smart contract sells collateral at current market value, using funds obtained to repay the outstanding loan amount for a fair and efficient debt recovery process.

Security and Gas Optimization Enhancements:
Access controls, encryption, decentralized storage solutions, and gas optimization techniques are implemented for enhanced collateral security, resilience, and efficient execution of liquidation processes.

In conclusion, this decentralized lending platform encompasses a comprehensive and secure ecosystem, offering borrowers and lenders a transparent, efficient, and trustworthy environment for financial interactions. The integration of cutting-edge technologies and best practices ensures a robust and resilient system that sets a new standard for decentralized finance.
