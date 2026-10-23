# CCLinkForge Pro (v1.0.0)

**CC-Link IE Field & CC-Link (CLPA / IEC 61158\) Gigabit Industrial Ethernet Protocol Studio, Cyclic Link Relay/Register (RY/RX/RWw/RWr) Engine, Transient SLMP/MC Protocol Command Builder, & 10-Point Industrial Network Safety Auditor**

---

## ⚡ Overview

**CCLinkForge Pro** is an industrial automation protocol engineering suite specifically targeted at **CC-Link IE Field**, **CC-Link IE TSN**, and legacy **CC-Link (IEC 61158 / CLPA)** networks. It provides zero-dependency, browser-based, and command-line automation for:

1. **SLMP (Seamless Message Protocol) 3E/4E Binary Frame Builder & Dissector**: Real-time packet crafting and decoding over UDP/IP (port 45237\) and TCP/IP.  
2. **Cyclic Link Matrix Engine**: Automatic calculation and contiguous hexadecimal address mapping for remote input bits (`RX`), remote output bits (`RY`), remote register writes (`RWw`), and remote register reads (`RWr`).  
3. **Gigabit Link Scan Time & Bandwidth Sizer**: Physical topology modeling incorporating station token passing overhead, preamble timings, cable propagation delays (\$5\\text{ ns/m}\$), and sub-millisecond determinism validation (\$T\_{\\text{scan}} \< 1.0\\text{ ms}\$).  
4. **10-Point Industrial Network Safety Auditor**: Pre-flight verification against CLPA BAP-0100/0105 standards, checking station ID ranges, duplicate bus addresses, memory buffer boundaries, Cat5e 100m segment limits, loopback ring redundancy, and timer safety margins.  
5. **PLC Configuration Exporter**: Immediate export to GX Works3 CSV parameter tables, IEC 61131-3 Structured Text global device blocks, and Python automation scripts.

---

## 📁 Repository Structure

product\_195/

├── source-code/

│   ├── cclink-frame-engine.js      \# SLMP 3E binary encoder, decoder & device maps

│   ├── cclink-link-matrix.js       \# Cyclic link memory mapping & scan time sizer

│   ├── cclink-network-auditor.js   \# 10-Point safety auditor engine

│   ├── cclink-forge.css           \# High-contrast dark industrial UI theme

│   ├── app.js                      \# Interactive workbench application controller

│   └── index.html                  \# Responsive 5-tab web studio

├── build/

│   ├── cclink-cli.py               \# Standalone Python CLI executable (chmod \+x)

│   └── cclinkforge-pro-v1.0.0.zip  \# Production distribution archive

├── documentation/

│   ├── ARCHITECTURE.md             \# Detailed engineering specifications & protocol math

│   ├── USER\_GUIDE.md               \# User guide, commands, and operator manual

│   ├── MONETIZATION\_AND\_MARKETING\_PLAYBOOK.md \# Pricing, licensing & GTM strategy

│   └── PROGRESS\_REPORT.md          \# Cycle \#195 delivery verification report

├── screenshots/

│   └── cclink-studio-preview.svg   \# High-resolution architectural vector diagram

└── README.md                       \# Master product documentation

---

## 🚀 Quick Start

### 1\. Launch Interactive Web Studio

Open `product_195/source-code/index.html` in any web browser. No server, node modules, or build steps required.

### 2\. Standalone Python CLI Usage

\# Make CLI executable

chmod \+x product\_195/build/cclink-cli.py

\# Build an SLMP 3E Binary Read Frame for Station 2 Remote Register Read (RWr)

./product\_195/build/cclink-cli.py slmp-build \--net 1 \--stn 2 \--cmd read \--dev RWr \--head 0 \--points 32

\# Dissect an SLMP Frame Hex Stream

./product\_195/build/cclink-cli.py slmp-dissect "50000101FF03000C001000010400000000009C1000"

\# Run 10-Point Network Safety Audit

./product\_195/build/cclink-cli.py audit \--stations '\[{"station":1,"rx":64,"ry":64,"rww":16,"rwr":16},{"station":2,"rx":32,"ry":32,"rww":32,"rwr":32}\]'

---

## 🧪 Verification & Automated Testing

The engine has been tested against 10 comprehensive unit tests:

python3 test\_cclinkforge.py

\# Output: Ran 10 tests in 0.484s \- OK

---

## 💼 Commercial & Pricing Model

- **Community Edition**: Free / Open Source (SLMP Builder & 4-Station Matrix).  
- **Professional License**: \$249 one-time per engineer seat (Full 10-Point Auditor, Python CLI, GX Works3 / ST Exporter).  
- **Enterprise / Site License**: \$1,890 / facility / year (Unlimited seats, custom dissector plugins, CI/CD validation hooks).