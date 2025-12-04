---
title: "Blog 3"
date: "2025-09-09T19:53:52+07:00"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---


# How Blocksee Built a Web3 CRM Using Blockchain Data from Amazon Managed Blockchain (AMB) Query  
**Authors:** Forrest Colyer & AJ Park  
**Published:** March 6, 2024  
**Categories:** Amazon Managed Blockchain, Blockchain, Customer Solutions, Foundational (100)

---

## About the Authors

**AJ Park** is a Product Manager on the Amazon Managed Blockchain team at AWS.  
With over 20 years of experience in data protection and storage as a software engineer and product manager, he is passionate about building blockchain and Web3 solutions for customers.

**Forrest Colyer** leads the Web3/Blockchain Specialist Solutions Architecture team supporting Amazon Managed Blockchain (AMB).  
He works with customers across all stages of blockchain adoption—from proof-of-concept to production—providing technical expertise and strategic direction for implementing impactful blockchain workloads.

---

# Overview

**Blocksee** provides a Web3-focused CRM and user engagement platform that delivers rich insights for NFT and crypto marketers.  
By embedding simple code into a website or using APIs, Blocksee enables marketers to collect data about users who interact with digital memberships, event tickets, and promotional assets.

Powered by AWS services—including **Amazon Managed Blockchain (AMB)**—Blocksee helps brands build:

- Loyalty programs  
- Token-gated content  
- Dynamic customer journeys  
- Automatic wallet creation via email  
- Onramp payments for receiving digital assets (e.g., NFTs)

To enable deep analytics on digital asset activity and user interactions, Blocksee requires massive amounts of **on-chain data** from public blockchains such as Ethereum, including:

- Current & historical token balances  
- Ownership of fungible and non-fungible tokens (NFTs)  
- User interactions with Web3 applications & smart contracts  

Blocksee evaluated multiple technical approaches—from operating its own full blockchain infrastructure to using third-party providers.  
Self-managed infrastructure proved too costly and operationally heavy due to:

- High compute, storage & networking demands  
- Resource-heavy ETL pipelines and indexing operations  
- Significant developer effort that slowed product feature delivery  

Third-party blockchain data providers were also insufficient, with challenges such as:

- Unreliable uptime  
- Poor data quality  
- Slow performance  
- High and unpredictable pricing  

---

# Why Blocksee Chose Amazon Managed Blockchain (AMB) Query

Blocksee ultimately adopted **AMB Query**, a unified blockchain data API for multiple public networks.

Benefits of switching:

### ✔ Higher reliability### ✔ Lower and predictable cost  
### ✔ Faster performance  
### ✔ A single, consistent API for multiple blockchains  

This allowed Blocksee to shorten product release cycles and reduce engineering overhead.

A statement from **Eric Forst, Co-founder & CEO of Blocksee**, highlights the transformation:

> “Before using Amazon Managed Blockchain, our team had to aggregate data from many different RPC providers, resulting in complex API configurations and monitoring overhead.  
> AMB changed everything — fast and stable access to blockchain data helped us streamline our system and rely on a more trustworthy infrastructure.”

---

# How Blocksee Uses AMB Query

When marketers or project managers open Blocksee CRM, token balance data for blockchain addresses (users) is displayed instantly and combined with additional context such as AI-driven behavioral analytics.

Blocksee uses the **ListTokenBalances API** from AMB Query to retrieve ERC-20 and ERC-721 token balances.  
The API allows Blocksee to:

- List all token balances belonging to a wallet or contract  
- List all token holders for a given smart contract  
- List balances for a specific token across all holders  

### ⭐ Result:  
**25% performance improvement**  
**50% cost reduction**  
compared to Blocksee’s previous token data retrieval mechanism.

Blocksee CTO **Matt Kotnik** shared additional insights:

> “We saw significant load time improvements—over 25% faster—using AMB Query’s ListTokenBalances API.  
> AMB also allows us to scale easily to additional blockchains thanks to Amazon’s chain-agnostic design.  
> This helps us focus more on our core product and customer relationships while relying on a trusted infrastructure partner.”

Because AMB Query uses a **standardized REST API**, integrating new blockchains in the future becomes simple.  
The query syntax remains nearly the same even when fetching data across multiple networks.

---

# Conclusion

AMB Query is now available in the **US East (N. Virginia)** Region, offering:

- Sub-second latency  
- Highly scalable access to blockchain balances & historical transactions  
- No need to operate blockchain infrastructure  
- Simple, predictable pricing based on API calls  

Customers can rely on AMB Query for high-performance, reliable blockchain data that meets the demands of real-world Web3 applications.

To learn more:

- Explore **AMB Query Documentation**  
- Explore other AMB services at **Amazon Managed Blockchain**