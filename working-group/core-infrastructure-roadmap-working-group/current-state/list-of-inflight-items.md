---
description: 'Published: 26/7/2024'
---

# List of Inflight items

{% hint style="info" %}
This page is written on behalf of the Core Infrastructure Roadmap working group, the information contained is subject to change and amendment by the working group at any time.
{% endhint %}

## Introduction

The objective of this document is to provide context for the inflight items within Intersect. This list was developed in collaboration with the various suppliers and item champions to encourage accuracy. At the end of this document, we will provide details of future planned work to improve this list further. If you like to read more of the progress on the milestones and deliverables, please refer to the milestone reports published [here](https://docs.intersectmbo.org/cardano/cardano-continuity/cardano-continuity-reports/what-work-has-been-completed-since-the-start-of-intersect).

{% hint style="info" %}
The CIR-wg recognises that public accessibility becomes inherently important as an Open Source environment, however not all documents linked below are publicly accessible - Please send a request to the document owners if you require access to view them!&#x20;
{% endhint %}

### 1. Cardano Onchain Governance - Voltaire Era (Pre-contracted)

Onchain governance is being implemented on Cardano by engaging with the Community in an open dialogue, the implementation is being carried out primarily by implementation of CIP-1694 on the Blockchain

CIP-1694 is implementing a set of Ledger rules to provide the following:

* expose a set of Governance Actions which will allow Community to create governance-actions which can be voted by Ada holders
* key management for Constitutional Committee (CC) - the CC is a selected group composed of founding and Community Members who opine on the validity of a raised Governance Action
* voted Delegated Representatives (DReps) who see voting power to represent smaller community Ada holders in a larger bloc and vote based on their view on the value of a 'proposed Cardano change' Implementation: IOI have been engaged to implement CIP-1694 based on work already being in-flight, and fitness to undertake the work as deemed by Technical Steering Committee (TSC) and community support for this work to be prioritized.

<table data-header-hidden><thead><tr><th width="245"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Decentralization|Regulatory Compliance|Ecosystem</td></tr><tr><td>Documentation</td><td><a href="https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694">https://github.com/cardano-foundation/CIPs/tree/master/CIP-1694</a></td></tr><tr><td>Target State</td><td>Onchain Voting available for community members</td></tr><tr><td>Definition of Done</td><td>Implementation + Documentation + Service Level Agreements</td></tr><tr><td>Product Stage</td><td>Write CIP | Proof of Concept | Research | Standalone, Prototype</td></tr><tr><td>Functional Requirements</td><td>Implement onchain voting using an agreed set of Governanace actions, provide interface to GovTool to vote as a DRep</td></tr><tr><td>Non-functional Requirements</td><td>Votes to be possible in the agreed epoch</td></tr><tr><td>External Dependencies</td><td>Tooling will need to be upgraded such as Wallets, Indexers to work with new Cardano Era</td></tr><tr><td>Communication Channel</td><td>Cardano update/Telegram/Twitter/Discord</td></tr><tr><td>Indicative Sizing</td><td>15L</td></tr><tr><td>Context of Indicative Sizing</td><td>This will require work on Ledger, Plutus and peripheral tool including wallets and indexers</td></tr><tr><td>Hardfork</td><td>Yes</td></tr><tr><td>Security Review</td><td>Yes</td></tr><tr><td>Code Audit</td><td>Yes</td></tr><tr><td>Community Endorsement</td><td>Yes</td></tr><tr><td>Feasibility Study Required?</td><td>Yes</td></tr><tr><td>Reviewing Working Group</td><td>Ledger Working Group</td></tr><tr><td>Core Infrastructure</td><td>Yes</td></tr><tr><td>Item Champion</td><td>IO Engineering</td></tr></tbody></table>

### 2. Increase Capability to store UTxOs on disk using LSM (Pre-contracted)

With the continued growth of the Cardano Blockchain Ledger, the need to move the ledger state from memory (RAM) to disk is ever more pressing and important. Once achieved, this will enable Cardano to reach Bitcoin scale in terms of the number of users & wallets and the size of the UTxO set. At the same time SPOs nodes and full node wallets will be able to function on commodity hardware, including cheap cloud instances. Until this is achieved however, the RAM use of full nodes will inexorably increase, with corresponding increased costs for SPOs and full node wallet users for ever-bigger hardware capacity.

The implementation of the LSM component is a crucial enabling step that provides the combination of features, performance and testability needed to support storing the bulk of the ledger state on disk. The LSM component itself is standalone. A follow-up stage of the project will be to fully exploit it within the node (in the consensus and ledger layers) to store all the large portions of the ledger state on disk, both the UTxO and the several stake-related tables.

The component itself takes the form of a Haskell library for managing tables of key-value data stored persistently on disk. The component is specified as a stand alone component, in isolation from Cardano, with detailed functional and non-functional requirements. These requirements have been chosen to support the scaling goals for Cardano. For example, one performance target is to have a table (corresponding to the characteristics of the UTxO) of 100 million entries - which is roughly the size of Bitcoin - while achieving certain throughput targets. The work is structured as a fixed price, fixed schedule contract, with fixed functional and non-functional requirements.

<table data-header-hidden><thead><tr><th width="234"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Scaling - making the node's RAM use (mostly) independent of the size of the ledger state should allow Cardano to reach Bitcoin scale in size (UTxO and total number of users/wallets)</td></tr><tr><td>Documentation</td><td>Whitepaper: <a href="https://drive.google.com/file/d/1XkY7CKNM9DoL4c8rbnAKUH6s9PUrJ5oH/view">https://drive.google.com/file/d/1XkY7CKNM9DoL4c8rbnAKUH6s9PUrJ5oH/view</a></td></tr><tr><td>Target State</td><td>Produce a new Log Structured Merge Tree implementation for Cardano.</td></tr><tr><td>Definition of Done</td><td>The criteria for demonstrating that the requirements are met are specified in the contract.</td></tr><tr><td>Product Stage</td><td>Full standalone product, but integration outstanding</td></tr><tr><td>Functional Requirements</td><td>Detailed functional requirements in the contract.</td></tr><tr><td>Non-functional Requirements</td><td>Detailed non-functional requirements in the contract.</td></tr><tr><td>External Dependencies</td><td>None, but using/integrating the LSM is a follow-up task.</td></tr><tr><td>Communication Channel</td><td><p>Intersect Development Updates</p><p>Intersect Knowledge Base</p></td></tr><tr><td>Indicative Sizing</td><td>L</td></tr><tr><td>Context of Indicative Sizing</td><td>Data estimated for total personnel x FTE based on milestones</td></tr><tr><td>Hardfork</td><td>Not required</td></tr><tr><td>Security Review</td><td></td></tr><tr><td>Code Audit</td><td></td></tr><tr><td>Community Endorsement</td><td>Nothing systematic or formal</td></tr><tr><td>Feasibility Study Required?</td><td>Covered already by the report "Storing the Cardano ledger state on disk: requirements for high performance backend", Version 0.9, July 2023</td></tr><tr><td>Reviewing Working Group</td><td>Node Working Group</td></tr><tr><td>Core Infrastructure</td><td>Yes</td></tr><tr><td>Item Champion</td><td>Well-Typed</td></tr><tr><td>Talking Points (Optional)</td><td>Scaling to Bitcoin size in terms of number of users &#x26; wallets, while still running on commodity hardware, and supporting future transaction throughput targets.</td></tr></tbody></table>

### 3. Implement Zero Knowledge proof (Pre-contracted)

With the growth Layer1 traffic, the ability to create a mechanism to allow the verification of information in a sidechain where all the underlying data is not necessarily needed, but a mechanism to ensure a high level of security, privacy and traceability is needed; this can be achieved using Zero Knowledge proofs

Halo 2 eliminates the need for a trusted setup. The development of Zero-knowledge proofs (ZKPs) increases future interoperability of the Cardano economy. This contract supports work on repeatedly refining proof obligations until a base obligation can be discharged. ZKPs will aid in the launch of Partner Chains or side chains to facilitate interoperability of Cardano as a whole, Galois work in collaboration with Intersect, IOI and the Electric Coin Company to implement recursion in a codebase Completed tasks, code deliverables, will be submitted for review via pull requests and will include unit and property based tests to improve quality. Pull requests will be made to the open source repository or the corresponding Privacy Scaling Explorations fork of the repository. All code deliverables will be implemented in Rust.

<table data-header-hidden><thead><tr><th width="229"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Interoperability - enabling the ability to trade between blockchains</td></tr><tr><td>Documentation</td><td><a href="https://github.com/input-output-hk/galois_recursion/tree/dev/book">https://github.com/input-output-hk/galois_recursion/tree/dev/book</a></td></tr><tr><td>Target State</td><td>Recursive ZKPs for IPA and KZG in Halo2</td></tr><tr><td>Definition of Done</td><td>Implementation + Documentation</td></tr><tr><td>Product Stage</td><td>Proof of Concept | Research | Standalone, Prototype</td></tr><tr><td>Functional Requirements</td><td>Rust implementations in Halo2 for the Poseidon SAFE spec, recursive PLONK verification, IPA folding, KZG folding, and Incrementally Verifiable Computation (IVC)</td></tr><tr><td>Non-functional Requirements</td><td>API for users to run IVC</td></tr><tr><td>External Dependencies</td><td>Rust packages: halo2curves, halo2_proofs</td></tr><tr><td>Communication Channel</td><td>Cardano update/Telegram/Twitter/Discord</td></tr><tr><td>Indicative Sizing</td><td>10L</td></tr><tr><td>Context of Indicative Sizing</td><td>This requires building all the components for recursion and IVC itself</td></tr><tr><td>Hardfork</td><td>No</td></tr><tr><td>Security Review</td><td>This is a cryptographic implementation to verify state without needing to know the entire state</td></tr><tr><td>Code Audit</td><td></td></tr><tr><td>Community Endorsement</td><td>Which community structure is involved?</td></tr><tr><td>Feasibility Study Required?</td><td>No</td></tr><tr><td>Reviewing Working Group</td><td>Plutus Working Group</td></tr><tr><td>Core Infrastructure</td><td>Yes (Plutus)</td></tr><tr><td>Item Champion</td><td>Galois</td></tr></tbody></table>

### 4. Enabling Documenting tools including Serialisation, Wallets and Education supporting Age of Voltaire (Pre-contracted)

With the age of Voltaire comes a new set of components, concepts and Governance mechanisms across Cardano, this deliverable includes upgrade of Yoroi Wallet, Serialisation library and also set of Education tools to usher in Voltaire.\
\
Q1 2024 to produce a number of high quality Educational Materials - A covering every aspect of the ‘Age of Voltaire’, with study guides, videos and webinars, this includes all things CIP 1694. This supports growth and understand in all community members new and old. The development and testing of Cardano Serialisation library, including the Cardano Serialisation library updates required for CIP 1694. This is a library, written in Rust, for serialization & deserialization of data structures used in Cardano's Haskell implementation of Alonzo along with useful supporting utility functions.

<table data-header-hidden><thead><tr><th width="216"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Conway-compatible CSL and both Yoroi Mobile and Extension to enabling users a smooth transition to the post-Chang hard fork. And Voltaire education series to educate the community about the governance era in Cardano including CIP-1694.</td></tr><tr><td>Documentation</td><td><a href="https://docs.google.com/document/d/1CwqclVqzQfhbOoBI1C1mX7CiZuf1qAFMGITekvhXNA4/edit?usp=sharing">Cardano Serialization Library</a>,<a href="https://docs.google.com/document/d/1zBaPh_BXRb9aQevv42HLaIcUan2vg80qr-DDKCCMJng/edit?usp=sharing"> Yoroi Extension Wallet</a>,<a href="https://docs.google.com/document/d/1CKasNVg4YLf9D1nZWRWzKB9TSO8fGRBOvKyL7kP4abU/edit?usp=sharing"> Yoroi Mobile Wallet</a>,<a href="https://docs.google.com/spreadsheets/d/1N0MfwjXHOf1JRi6sYGbm2-nfCgdgUNjw5VU0Qy1wOUw/edit?usp=sharing"> Education</a> (WIP)</td></tr><tr><td><br></td><td>Project stemmed from CIP-1694</td></tr><tr><td>Target State</td><td>Upgraded CSL Library, Yoroi (Extension &#x26; Wallet) to support Conway Ledger Era, and launched educational series to explain all things Voltaire including CIP 1694</td></tr><tr><td>Definition of Done</td><td>All the items mentioned are upgraded, the final video series are uploaded to EMURGO Education Platform.</td></tr><tr><td>Product Stage</td><td>Standalone, Prototype</td></tr><tr><td>Functional Requirements</td><td>Accessible and maintained CSL builds with Conway functionality, Conway and CIP-95 being released in Yoroi wallets and extensions.</td></tr><tr><td>Non-functional Requirements</td><td>Education videos to be released in online education platform and being branded accordingly</td></tr><tr><td>External Dependencies</td><td>TBC</td></tr><tr><td>Communication Channel</td><td>EMURGO &#x26; Intersect Communication Channels</td></tr><tr><td>Indicative Sizing</td><td>-</td></tr><tr><td>Context of Indicative Sizing</td><td>-</td></tr><tr><td>Hardfork</td><td>Yes for some items and No for some</td></tr><tr><td>Security Review</td><td>N/A</td></tr><tr><td>Code Audit</td><td>N/A</td></tr><tr><td>Community Endorsement</td><td>No</td></tr><tr><td>Feasibility Study Required?</td><td>Yes</td></tr><tr><td>Reviewing Working Group</td><td>TBC</td></tr><tr><td>Core Infrastructure</td><td>Yes</td></tr><tr><td>Item Champion</td><td>EMURGO</td></tr></tbody></table>

### 5. Implementing the Ouroboros Genesis protocol (Pre-contracted)

Genesis is a new version of the Consensus layer that allows new nodes to join the network without requiring a trusted set of peers to bootstrap from. This should ultimately allow decommissioning the core relays.

All implementation work, in addition to appropriate testing, benchmarking, and documentation is a continuation of work from 2023. This covers the remaining testing infrastructure, as well as the full system test suite designed to verify and validate the Genesis implementation.

<table data-header-hidden><thead><tr><th width="213"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Interoperability &#x26; Transparency - enables new nodes to join the Cardano blockchain and bootstrap themselves without relying on a trusted service</td></tr><tr><td>Documentation</td><td><p>Whitepaper -<a href="https://eprint.iacr.org/2018/378.pdf"> https://eprint.iacr.org/2018/378.pdf</a></p><p><a href="https://iohk.io/en/blog/posts/2023/02/09/ouroboros-genesis-enhanced-security-in-a-dynamic-environment/">https://iohk.io/en/blog/posts/2023/02/09/ouroboros-genesis-enhanced-security-in-a-dynamic-environment/</a></p><p><a href="https://iohk.io/en/blog/posts/2024/05/08/ouroboros-genesis-design-update/">https://iohk.io/en/blog/posts/2024/05/08/ouroboros-genesis-design-update/</a></p></td></tr><tr><td>Target State</td><td>Stipulated in the Contract</td></tr><tr><td>Definition of Done</td><td>Stipulated in the Contract</td></tr><tr><td>Product Stage</td><td>Testing and benchmarking</td></tr><tr><td>Functional Requirements</td><td>Stipulated in the Contract</td></tr><tr><td>Non-functional Requirements</td><td>Stipulated in the Contract</td></tr><tr><td>External Dependencies</td><td>NA</td></tr><tr><td>Communication Channel</td><td>NA</td></tr><tr><td>Indicative Sizing</td><td>Stipulated in the Contract</td></tr><tr><td>Context of Indicative Sizing</td><td>Stipulated in the Contract</td></tr><tr><td>Hardfork</td><td>Not required</td></tr><tr><td>Security Review</td><td>Y</td></tr><tr><td>Code Audit</td><td>Y</td></tr><tr><td>Community Endorsement</td><td>N/A</td></tr><tr><td>Feasibility Study Required?</td><td>N/A</td></tr><tr><td>Reviewing Working Group</td><td>Node Working Group</td></tr><tr><td>Core Infrastructure</td><td>Yes</td></tr><tr><td>Item Champion</td><td>Tweag</td></tr></tbody></table>

### 6. Deliver an Open Source methodology for Cardano (Pre-contracted)

The Open Source Office (OSO) and the Open Source Committee (OSC) are tasked with ensuring Core Cardano becomes efficiently open sourced by creating a strategy (OSS) to curtail the situation.

Intersect, since January, took ownership of 27 “Core-Cardano” repos which are very centralized in nature from previous IOG management. There are strategies and policies in place but need to undergo testing and evaluation with reference to their implementation. Tweag is contracted to support bodies of work done by the Intersect OSPO.

<table data-header-hidden><thead><tr><th width="221"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Make Cardano truly Open Source<br>Develop open Source Strategy with OSC<br>Help get OSO fully functional</td></tr><tr><td>Documentation</td><td><a href="https://intersect.gitbook.io/open-source-committee/open-source-strategy">Strategy</a>,<a href="https://intersect.gitbook.io/open-source-committee/about/open-source-program-office-ospo"> OSO</a>,<a href="https://intersect.gitbook.io/open-source-committee/about/2024-ospo-roadmap"> OSO Roadmap</a>,<a href="https://intersect.gitbook.io/open-source-committee/policies/governance"> Governance Policy</a>,<a href="https://docs.google.com/document/d/1Ug39Lfgl9XcFp9SpmH-Qs4MEn1eindAtLx0rfQVPsJ8/edit#heading=h.4rnjpobxf8xe"> Security Policy</a>,<a href="https://docs.google.com/document/d/1V6Bnlq2X1VyLwnmiqNYicUIwLs5yGSKuAL6Iz9xSnhg/edit"> Project Framework Policy</a>,<a href="https://docs.google.com/document/d/1TJfIExc-AcqkB9gunVbDtK2bRR6ZOEXQHWouBEStSuM/edit#heading=h.w90hncqgai7h"> Project Incubation Process</a>,<a href="https://docs.google.com/document/d/13FU45CIoRt3YWQ-7KMsAXTFsxVJBVtg_/edit#heading=h.5cnfhn9b3opr"> Maintainer Pilot</a>,<a href="https://docs.google.com/document/d/1ASr_-0fX361VbI46ti2fmGNN5rlWYbOB6ZQ2bTLVieI/edit#heading=h.jmv6vldi3aw7"> OS Pilot</a></td></tr><tr><td>Target State</td><td>Open Source Strategy, Pilot to test strategy, and operational Open Source Office</td></tr><tr><td>Definition of Done</td><td>OSC adopted Strategy and fully operational open source office according to<a href="https://docs.google.com/presentation/d/1FqQ5mwt1qg3Wq3pvasdT3KyxvHUBgKChhaV__ge7tq4/edit"> these slides</a>, Pilot program to test open source maturity</td></tr><tr><td>Product Stage</td><td>Not Applicable, but delivery fully matured</td></tr><tr><td>Functional Requirements</td><td>Staff the OSO to support core delivery service, have OSC adopt a strategy, and coordinate OS pilot</td></tr><tr><td>Non-functional Requirements</td><td>Help with various items the OSO has in works</td></tr><tr><td>External Dependencies</td><td>Open Source Office Staff, Open Source Committee</td></tr><tr><td>Communication Channel</td><td>Discord, Gitbook, Github</td></tr><tr><td>Indicative Sizing</td><td>N/A</td></tr><tr><td>Context of Indicative Sizing</td><td>N/A</td></tr><tr><td>Hardfork</td><td>N/A</td></tr><tr><td>Security Review</td><td>N/A, but did assist in drafting of security policy for Intersect drafted<a href="https://docs.google.com/document/d/1Ug39Lfgl9XcFp9SpmH-Qs4MEn1eindAtLx0rfQVPsJ8/edit#heading=h.4rnjpobxf8xe"> here</a></td></tr><tr><td>Code Audit</td><td>N/A</td></tr><tr><td>Community Endorsement</td><td>Yes, OSC Adoption and Community Feedback into Open Source Strategy</td></tr><tr><td>Feasibility Study Required?</td><td>Yes, OSC Adoption and Community Feedback into Open Source Strategy</td></tr><tr><td>Reviewing Working Group</td><td>Open Source Committee, Strategy Working Group (now closed, due to task completion)</td></tr><tr><td>Core Infrastructure</td><td>Support Core Infra in open Source development practices</td></tr><tr><td>Item Champion</td><td>Tweag</td></tr><tr><td>Talking Points (Optional)</td><td>Everything to be done by End of Q2, only pilot results remain to be published.</td></tr></tbody></table>

### 7. Implementation of GovTool user journeys (Pre-contracted)

{% hint style="info" %}
Disclaimer: The development of Govtool consists of contracts with multiple vendors, there’s pending work to split this out by vendors. This item presents the implementation from Byron
{% endhint %}

GovTool is a webApp that implements key governance tools for important governance user journeys. Two key flows; DRep Explorer flow, Governance Action Submission flow, will be added in order to deliver a usable tool to the Cardano Community.

This implementation was previously worked on and will be continued by supporting the launch and running a beta testing period to discover and fix bugs, collect feedback and ideas for the community.

<table data-header-hidden><thead><tr><th width="213"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Collective governance, Interoperability, Transparency</td></tr><tr><td>Documentation</td><td><p>CIP-95 :<a href="https://github.com/cardano-foundation/CIPs/tree/master/CIP-0095"> https://github.com/cardano-foundation/CIPs/tree/master/CIP-0095</a></p><p>CIP-105:<a href="https://github.com/cardano-foundation/CIPs/tree/master/CIP-0105"> https://github.com/cardano-foundation/CIPs/tree/master/CIP-0105</a></p></td></tr><tr><td>Target State</td><td>An MVP governance system</td></tr><tr><td>Definition of Done</td><td>N/A</td></tr><tr><td>Product Stage</td><td>Prototype</td></tr><tr><td>Functional Requirements</td><td><p>Users able to delegate to DReps, </p><p>DReps able to vote on Governance Action</p></td></tr><tr><td>Non-functional Requirements</td><td>N/A</td></tr><tr><td>External Dependencies</td><td>Cardano Node (Conway Era)</td></tr><tr><td>Communication Channel</td><td>Ryan Williams</td></tr><tr><td>Indicative Sizing</td><td>L</td></tr><tr><td>Context of Indicative Sizing</td><td>UI build, integration components</td></tr><tr><td>Hardfork</td><td>Yes - it requires Chang Hardfork</td></tr><tr><td>Security Review</td><td>No</td></tr><tr><td>Code Audit</td><td>No</td></tr><tr><td>Community Endorsement</td><td>Supported by Community</td></tr><tr><td>Feasibility Study Required?</td><td>No</td></tr><tr><td>Reviewing Working Group</td><td>Governance Tool Working Group</td></tr><tr><td>Core Infrastructure</td><td>Yes</td></tr><tr><td>Item Champion</td><td>Byron</td></tr></tbody></table>

### 8. Ensure interoperability, performance and accessibility of Hardware Wallets (Pre-contracted)

The Ledger devices and Trezor devices are the most popular products on the market for secure management of cryptocurrencies - to ensures its continued practicality and use for the Cardano community a number of enhancements have been contracted.

Work is done to ensure the continued practical use of the Ledger and Trezor hardware wallets for the Cardano community and enhancements to support the Conway era.

<table data-header-hidden><thead><tr><th width="211"></th><th></th></tr></thead><tbody><tr><td>Drivers</td><td>Provide desired level of security to Voltaire era governance participants<br>Increase participation in governance by enabling most popular HW wallet holders to participate with HW wallet</td></tr><tr><td>Documentation</td><td>CIP-95 :<a href="https://github.com/cardano-foundation/CIPs/tree/master/CIP-0095"> https://github.com/cardano-foundation/CIPs/tree/master/CIP-0095</a></td></tr><tr><td>Target State</td><td>Trezor and Ledger owners are able to fully participate in Cardano on-chain governance</td></tr><tr><td>Definition of Done</td><td>Released by Ledger and Trezor in production</td></tr><tr><td>Product Stage</td><td><p>Trezor - released</p><p>Ledger - waiting for release (planned 7/2024)</p></td></tr><tr><td>Functional Requirements</td><td><p>Update following codebases and documentation to enable CIP-95.</p><p>Ledger’s Cardano app device firmware</p><p>Ledger’s Cardano App Javascript interface</p><p>Trezor’s device firmware</p><p>Trezor’s Connect Suite</p><p>Cardano HW wallet interoperability library</p><p>Cardano HW Wallet CLI</p><p>Cardano Improvement Proposal 21</p><p></p><p>Analyze and implement following:</p><p>Voltaire/Conway analysis</p><p>Stake (de)registration with deposit</p><p>Delegation to DReps</p><p>Serialization with tag 258</p><p>Redesign of certificate-related code</p><p>New key derivation schemas (for Ledger except for Nano S)</p><p>DRep registration (for Ledger except for Nano S)</p><p>Committee certificates (for Ledger except for Nano S)</p><p>Voting (for Ledger except for Nano S)</p><p>Treasury and donations (for Ledger except for Nano S)</p><p>Integration Layer</p></td></tr><tr><td>Non-functional Requirements</td><td>Communication with Ledger, Trezor, security auditors and other stakeholders; project management; npm releases</td></tr><tr><td>External Dependencies</td><td>Ledger &#x26; Trezor release process</td></tr><tr><td>Communication Channel</td><td>Slack, Email</td></tr><tr><td>Indicative Sizing</td><td>S</td></tr><tr><td>Context of Indicative Sizing</td><td>0.75 FTE x 9 months</td></tr><tr><td>Hardfork</td><td>No</td></tr><tr><td>Security Review</td><td>Not related directly to Cardano blockchain security but relevant for overall Cardano governance security</td></tr><tr><td>Code Audit</td><td>Yes - Ledger code audited by Kudelski, Trezor code audited by Trezor team</td></tr><tr><td>Community Endorsement</td><td>Not directly but related project had great Catalyst support<a href="https://projectcatalyst.io/funds/10/f10-products-and-integrations/message-signing-for-trezor-and-ledger-cip-8-cip30"> https://projectcatalyst.io/funds/10/f10-products-and-integrations/message-signing-for-trezor-and-ledger-cip-8-cip30</a></td></tr><tr><td>Feasibility Study Required?</td><td>No</td></tr><tr><td>Reviewing Working Group</td><td>N/A</td></tr><tr><td>Core Infrastructure</td><td>Related to core Cardano infrastructure as all the big Cardano holders use Trezor or Ledger</td></tr><tr><td>Item Champion</td><td>Vacuumlabs</td></tr></tbody></table>

### Future works planned

With what info we had, we were able to produce this list. Working with our suppliers, we were able to solicit earnest and insightful feedback as to how we can improve the list further. Here are some updates that we’re working on to include for future items:\
1\) Work Breakdown Structure\
2\) Business Benefit\
3\) Team Structure\
4\) Testing and Verification\
5\) Counterparty requirements\
6\) Impacted code structure:\
7\) Integration strategy\
8\) Dependencies\
9\) Artifacts/Deliverables that will be generated (beyond code)\
10\) Breaking down items based on objectives and contracts