# Hushed - A Secure, Private Chat System

Hushed is a privacy-focused, terminal-based chat system that leverages blockchain technology and zero-knowledge proofs (zk-SNARKs) to authenticate users securely and privately. It uses Solana for creating PDAs representing each chat session, Kafka to store recent chat messages, Arweave to store mature messages, and a groth16 zk-SNARK to validate user identity via a homogenous solution for checking the user credentials.

## Key Features

- **Solana PDA:** Hushed creates a PDA for each chat based on the combination of **user IDs** and **wallet IDs**. The PDA ID ensures that only valid users can participate in the chat.
  
- **zk-SNARK Authentication:** Using the **Groth16** zk-SNARK protocol, the system checks whether a user is valid by comparing a hashed combination of the user's ID and wallet ID against the token ID. This ensures only authorized users can access the chat.
  
- **Kafka-based Messaging:** Recent messages are stored in a **Kafka** broker, while older messages are compressed and stored directly on-chain.

- **Secure and Private:** Each user can only have one active chat. If they want a new chat, they must destroy the old one. All communication occurs securely between two users.

- **Transaction Fees:** The program charges transaction fees for minting and for storing messages once a set number of messages are reached (e.g., 100 or 1000 messages). Users need to ensure their wallet has sufficient funds to operate.

- **CLI-based Interface:** Users interact with the system directly from their terminal, making it lightweight and privacy-focused.

## Installation

To install and use **Hushed**, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/HamaJjigae/hushed.git
   cd hushed

2. Build the project with Cargo:
    cargo build --release

3. Install the program to run in your terminal:
    cargo install --path .

4. Run the program in your terminal:
    hushed

How It Works:

Technologies Used:
    Solana SDK: Used to create PDAs for each chat
    Poseidon Hashing: To securely hash user IDs and wallet IDs
    zk-SNARK (groth16): For ZKP authentication
    Kafka: For sotring and handling recent chat messages
    Bellperson: Rust crate with zk-SNARK support
    Blstrs: To assist with cryptographic operations.
