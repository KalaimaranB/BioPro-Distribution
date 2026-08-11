# 🧬 BioPro Distribution Registry

[![Security](https://img.shields.io/badge/Security-Cryptographic-success.svg)](#)
[![Status](https://img.shields.io/badge/Registry-Active-brightgreen.svg)](#)

Welcome to the **BioPro Distribution Registry**. This repository serves as the official decentralized index for discovering the **BioPro Core Application** updates and its suite of advanced scientific analysis plugins. It also provides the root cryptographic authority for the core system.

---

## 📂 Core Registry Files

*   **[`registry.json`](registry.json)**: The official pointer index. In version 2, this file strictly maps plugin IDs to their source repositories (`repo_url`). The BioPro Core application uses this file to eagerly fetch live plugin metadata (versions, descriptions, authors, etc.) directly from each plugin's `pyproject.toml`.
*   **[`authorities.json`](authorities.json)**: The root cryptographic trust-store containing the public key for the authorized core publisher (`BioPro Core Authority`).

---

## 🔌 Decentralized Plugin Architecture

BioPro relies on a decentralized, eagerly-loaded architecture for plugins. 

1. **Discovery**: The Core App reads `registry.json` from this repository to discover approved plugins.
2. **Metadata Fetching**: For each plugin, it dynamically fetches the `pyproject.toml` manifest from the plugin's GitHub repository.
3. **Decentralized Trust**: Developer keys, CI/CD identities, and signatures are hosted and maintained by the plugins themselves. The core verifies that a plugin's author key chains up to a trusted root, and that the CI bot signing the plugin releases is delegated by that author.
4. **Caching & Refreshing**: Plugin metadata and download URLs are cached locally with a TTL, keeping store performance fast while allowing manual invalidation via the UI.

---

## 🔒 Security & Verification

To maintain security and integrity, BioPro validates all downloads using public-key cryptography.

| Authority Name | Authority ID | Public Key (SHA-256) |
| :--- | :--- | :--- |
| **BioPro Core Authority** | `biopro_core` | `08f4319b6f979057b36b0db2b8faaee6eff8782f3aafd5e924ba79b04d4c8366` |

Plugin authors receive cryptographic signatures from the Core Authority. In turn, plugin authors can delegate trust to CI bots to automate package signing during releases.
