# 🔐 PassGuard — Password Policy Analyzer & GRC Compliance Tool

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100.0-009688?style=for-the-badge&logo=fastapi)
![Security](https://img.shields.io/badge/Type-GRC%20%26%20Compliance-purple?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **Project 5 of 10 — Industrial Cybersecurity Suite**
> Real-time password analyzer, GRC compliance checker, policy generator, and bulk auditor covering NIST SP 800-63B, PCI-DSS 4.0, ISO 27001, and HIPAA.

---

## 🎯 Overview

PassGuard goes beyond simple strong/weak indicators. It calculates Shannon entropy, estimates real crack times using GPU benchmarks, checks compliance against 4 major security standards, generates full GRC policy documents, and audits 100 passwords at once.

---

## ✨ Features

| Module | Description |
|--------|-------------|
| 🔍 **Real-time Analyzer** | Instant strength score as you type |
| 📊 **Shannon Entropy** | Mathematically accurate entropy in bits |
| ⏱️ **Crack Time Estimator** | Online / bcrypt / 100B sec GPU |
| ✅ **Compliance Checker** | NIST SP 800-63B, PCI-DSS 4.0, ISO 27001, HIPAA |
| ⚡ **Password Generator** | Random + passphrase mode with strength preview |
| 📋 **Policy Builder** | Full GRC policy document with one click |
| 📦 **Bulk Audit** | Analyze 100 passwords with visual report |
| 🔒 **Common Password Check** | Flags known breached passwords |
| 🌐 **Works Offline** | Full analysis runs in browser — no backend needed |

---

## 🚀 Quick Start

```bash
cd backend
python -m venv venv
venv\Scripts\activate       # Windows
pip install -r requirements.txt
python -m uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```
Open `frontend/index.html` — works immediately even without backend.

---

## 🔌 API Reference

### `POST /password/analyze`
```json
{ "password": "MyP@ssw0rd123!" }
```
Returns: score, entropy, crack times, compliance, suggestions.

### `POST /password/bulk`
```json
{ "passwords": ["password123", "MyP@ss!123", "correct-horse-battery"] }
```

### `POST /policy/generate`
```json
{ "org_name": "Acme Corp", "standard": "pci_dss_4", "min_length": 12, "require_mfa": true }
```
Returns: full GRC policy text document.

---

## 🧠 How It Works

### Shannon Entropy
```
Entropy = Length × log₂(CharsetSize)
```
| Charset | Size |
|---|---|
| Lowercase only | 26 |
| + Uppercase | 52 |
| + Numbers | 62 |
| + Symbols | 94 |

### Crack Time
```
Time = (N^L) / 2 / guesses_per_second
```
| Attack | Speed |
|---|---|
| Online throttled | 100/sec |
| Offline bcrypt | 10M/sec |
| GPU cluster | 100B/sec |

### Compliance
| Standard | Min Len | Key Rule |
|---|---|---|
| NIST SP 800-63B | 8 | Block common passwords |
| PCI-DSS 4.0 | 12 | Upper + Number + Symbol |
| ISO 27001 | 12 | 3+ character types |
| HIPAA | 8 | Mixed types |
