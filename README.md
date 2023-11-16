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
