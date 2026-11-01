LayerNFT: A Decentralized NFT Marketplace on Ethereum

!Stars !Fork !PRs !License

<img src="https://img.shields.io/badge/-Next_JS-black?style=for-the-badge&logoColor=white&logo=nextdotjs&color=000000" alt="Next.js" />
<img src="https://img.shields.io/badge/-TypeScript-black?style=for-the-badge&logoColor=white&logo=typescript&color=3178C6" alt="TypeScript" />
<img src="https://img.shields.io/badge/-Tailwind_CSS-black?style=for-the-badge&logoColor=white&logo=tailwindcss&color=06B6D4" alt="Tailwind CSS" />
<img src="https://img.shields.io/badge/-Solidity-black?style=for-the-badge&logoColor=white&logo=solidity&color=363636" alt="Solidity" />
<img src="https://img.shields.io/badge/-The_Graph-black?style=for-the-badge&logoColor=white&logo=thegraph&color=6747ED" alt="The Graph" />
<img src="https://img.shields.io/badge/-Hardhat-black?style=for-the-badge&logoColor=white&logo=hardhat&color=FFF100" alt="Hardhat" />
<img src="https://img.shields.io/badge/-IPFS-black?style=for-the-badge&logoColor=white&logo=ipfs&color=65C2CB" alt="IPFS" />

Overview

LayerNFT is a full-stack NFT marketplace built on the Ethereum Sepolia network, designed to provide a decentralized platform for creating, trading, and managing NFTs. Users can mint NFTs into their own collections, create fixed-price listings, participate in on-chain auctions, submit and accept offers, and monitor marketplace activity through a real-time indexed subgraph — without relying on a centralized backend.

The platform follows a custody-based escrow approach. When an NFT is listed, ownership is transferred to the marketplace contract. The NFT is then returned to the seller if the listing is cancelled or transferred to the buyer once a purchase is completed.

Demo
Screenshots coming soon. Add a public deployment URL and showcase images here once available.
Features
NFT Minting — Upload images and metadata, including names, descriptions, and traits, to IPFS through Pinata and mint NFTs into collections you own.
Collection Creation — Deploy custom ERC-721 collections directly on-chain with adjustable royalty settings, maximum supply, and minting prices.
Fixed-Price Trading — Create, cancel, and modify NFT listings, with automatic distribution of royalties and marketplace fees during purchases.
On-Chain Auctions — Start time-limited auctions with reserve prices, track bidding activity, and automatically refund previous bidders when they are outbid.
NFT Offers — Submit, cancel, and accept offers for indexed NFTs, with automatic expiration for inactive offers.
User Profiles — Explore your owned NFTs, current listings, submitted offers, and received offers in one place.
Live Activity Updates — Marketplace events are indexed using The Graph Protocol subgraph, providing up-to-date data without continuous polling.
Seller-Friendly Interface — Sellers are shown cancellation options instead of purchase or offer actions, with the same restrictions enforced by the smart contracts.
Architecture
text
nft-marketplace/
├── contracts/      Solidity — LayerMarketplace, NFTCollection, CollectionFactory
├── subgraph/       The Graph — AssemblyScript event handlers + GraphQL schema
└── frontend/       Next.js 14 App Router — wagmi, viem, TanStack Query, Tailwind

Tech Stack
Layer	Technology
Smart Contracts	Solidity 0.8.28, Hardhat, OpenZeppelin
Indexing	The Graph Protocol (AssemblyScript)
Frontend	Next.js 14, TypeScript, Tailwind CSS
Web3 Integration	wagmi v2, viem, RainbowKit
Decentralized Storage	IPFS via Pinata
Data Management	TanStack Query, graphql-request
Blockchain Network	Ethereum Sepolia
Getting Started
Prerequisites

Before running the project, make sure you have the following installed or configured:

Node.js 18 or later
pnpm package manager
A wallet private key for deploying smart contracts
Pinata API credentials for uploading files to IPFS
A Graph Studio account
1. Clone the Repository
bash
git clone https://github.com/AayushmanThapaMagar/Layer-NFT-Marketplace.git
cd Layer-NFT-Marketplace

2. Set Up Smart Contracts
bash
cd contracts
pnpm install
cp .env.example .env   # Configure PRIVATE_KEY and RPC_URL
pnpm hardhat run scripts/deploy.ts --network sepolia

3. Configure the Subgraph
bash
cd subgraph
pnpm install
# Add the deployed contract addresses to subgraph.template.yaml
graph codegen && graph build
graph deploy <your-subgraph-slug>

4. Run the Frontend
bash
cd frontend
pnpm install
cp .env.example .env.local   # Configure contract addresses, Graph URL, and Pinata credentials
pnpm dev


Once the development server starts, open http://localhost:3000 in your browser.

Environment Variables
frontend/.env.local
env
NEXT_PUBLIC_MARKETPLACE_ADDRESS=0x...
NEXT_PUBLIC_COLLECTION_FACTORY_ADDRESS=0x...
NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID=...
GRAPH_API_URL=https://api.studio.thegraph.com/query/.../version/latest
PINATA_API_KEY=...
PINATA_API_SECRET=...

contracts/.env
env
PRIVATE_KEY=0x...
SEPOLIA_RPC_URL=https://...
ETHERSCAN_API_KEY=...

Author

Hyrum Perez

GitHub: @AayushmanThapaMagar
Project Repository: Layer-NFT-Marketplace
License

This project is distributed under the MIT License.