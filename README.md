# 🧬 BioPro Distribution Registry

[![Aesthetics](https://img.shields.io/badge/Aesthetics-Premium-blueviolet.svg)](#)
[![Security](https://img.shields.io/badge/Security-Cryptographic-success.svg)](#)
[![Status](https://img.shields.io/badge/Registry-Active-brightgreen.svg)](#)

Welcome to the centralized **BioPro Distribution Registry**. This repository serves as the official single-source-of-truth for distributing and updating the **BioPro Core Application** and its suite of advanced scientific analysis plugins. It also provides the cryptographic authorities used to verify the integrity and origin of updates.

---

## 📂 Core Registry Files

*   **[`registry.json`](file:///Users/kalaimaranbalasothy/GitHub%20Projects/BioPro-Distribution/registry.json)**: The official index of available releases, containing version tracking, release notes, and download URLs for both the BioPro Core and official plugins.
*   **[`authorities.json`](file:///Users/kalaimaranbalasothy/GitHub%20Projects/BioPro-Distribution/authorities.json)**: The cryptographic trust-store containing public keys for authorized publishers (e.g., `BioPro Core Authority`) to prevent unauthorized plugin distribution and tampering.

---

## 📱 Core Application Status

| Property | Value |
| :--- | :--- |
| **Current Version** | `1.0.1` |
| **Release Notes** | *Updated release with dynamic plugin architecture.* |
| **Download URL** | [Latest Core Release](https://github.com/KalaimaranB/BioPro/releases/latest) |

---

## 🔌 Registered Scientific Plugins

| Plugin ID | Plugin Name | Version | Min. Core Version | Description | Author | Download Link |
| :--- | :--- | :---: | :---: | :--- | :--- | :---: |
| **`western_blot`** | Western Blot Densitometry | `1.0.7` | `1.0.4` | Automated lane detection, band quantification, and Ponceau normalization. | Kalaimaran Balasothy | [Download ZIP](https://github.com/KalaimaranB/BioPro-Plugins/releases/download/western_blot/v1.0.7/western_blot.zip) |
| **`cytometrics`** | CytoMetrics | `0.1.7` | `1.0.4` | AI-assisted multi-channel cell morphology quantification. | Kalaimaran Balasothy | [Download ZIP](https://github.com/KalaimaranB/BioPro-Plugins/releases/download/cytometrics/v0.1.7/cytometrics.zip) |
| **`flow_cytometry`** | Flow Cytometry Workspace | `0.2.1` | `1.0.4` | Scientist-centric flow cytometry analysis with FMO-guided gating, adaptive gates, workflow templates, and full workspace control. | Kalaimaran Balasothy | [Download ZIP](https://github.com/KalaimaranB/BioPro-Plugins/releases/download/flow_cytometry/v0.2.1/flow_cytometry.zip) |

---

## 🔒 Security & Verification

To maintain security and integrity, BioPro validates all downloads using public-key cryptography. The following authorities are trusted to sign releases:

| Authority Name | Authority ID | Public Key (SHA-256) |
| :--- | :--- | :--- |
| **BioPro Core Authority** | `biopro_core` | `08f4319b6f979057b36b0db2b8faaee6eff8782f3aafd5e924ba79b04d4c8366` |

*Last Updated: 2026-05-06T14:32:22Z*

---

## ⚙️ How it Works

The BioPro Core App periodically polls this registry to:
1. **Check for Updates**: It compares local core/plugin versions against those specified in `registry.json`.
2. **Validate Signatures**: Before installing any downloaded `.zip` package, it verifies the cryptographic signature against the public keys listed in `authorities.json`.
3. **Seamlessly Install**: If the signature matches a trusted authority, the update is dynamically hot-reloaded into the user's workspace.
