# Cluster Prototype - GPU Cluster Build Documentation

## Project Overview

**Objective:** Build a distributed GPU cluster for AI model inference using available hardware
**Team:** Sameer and Ismaiel
**Hardware:** 2x RTX 5070 GPUs across 2 separate PCs
**Primary Use Case:** Distributed AI inference for running large language models (Llama models)
**Assigned By:** JB

---

## Phase 1: Initial Windows Attempt with Exo

### Hardware Setup
- **PC 1:** RTX 5070 GPU (Windows)
- **PC 2:** RTX 5070 GPU (Windows)
- **Network:** Local network connection between PCs

### Software Stack
- **Clustering Framework:** Exo (distributed inference framework)
- **Operating System:** Windows 10/11
- **Background:** Previous experience with Linux-based clustering using Exo

### Issues Encountered

#### 1. Windows Dependency Problems
When attempting to run Exo on Windows, we encountered multiple dependency issues:
- **Python Package Dependencies:** Missing or incompatible Python libraries required by Exo
- **CUDA/GPU Driver Issues:** Problems with GPU detection or CUDA toolkit compatibility
- **Networking Libraries:** Network communication dependencies not properly configured for Windows

**Status:** Unable to resolve dependencies natively on Windows

---

## Phase 2: WSL (Windows Subsystem for Linux) Attempt

### Approach
Installed WSL to leverage Linux environment while staying on Windows host.

### Issues Encountered
- **Environment Configuration Issues:** Exo dependencies and environment setup failed in WSL
- **GPU Passthrough:** Potential issues with GPU access through WSL layer
- **Network Discovery:** Unable to establish node-to-node communication

**Attempted Solutions:**
- Set up complete Exo environment in WSL
- Configured networking settings
- Attempted to connect 2 nodes together

**Status:** Failed - could not successfully connect the 2 nodes together

---

## Phase 3: Modified Windows Configuration (Partial Success)

### Breakthrough
Used AI tools to modify Exo configuration files to make it compatible with Windows environment.

### Success
- **Initial Connection:** Successfully got Exo running on Windows
- **Single Node Detection:** Each PC could detect its own GPU and initialize
- **Problem:** Only showing 1 node on each PC (not connecting as a cluster)

### Network Configuration Fix
**Issue:** Windows Firewall was blocking inter-node communication
**Solution:** Disabled Windows Firewall on both PCs

**Result:** Successfully established cluster connection between the 2 PCs

---

## Phase 4: Model Download Loop Issue

### Test Configuration
- **Model:** Llama model (large language model)
- **Status:** Cluster successfully connected with 2 nodes visible
- **Network:** Both GPUs communicating properly

### Critical Issue
**Problem:** Model downloading process entered an infinite loop
- Download would start but never complete
- Process would restart and loop indefinitely
- Unable to actually run inference

### Troubleshooting Attempts
1. **Restart Everything:** Restarted both PCs and Exo processes
2. **Result:** Same download loop issue persisted
3. **Conclusion:** Fundamental issue with Exo's Windows implementation

---

## Phase 5: Second WSL Attempt (Final Windows Attempt)

### Motivation
Attempted WSL again with better understanding of previous issues.

### Setup Process
- Reinstalled and configured WSL environment
- Set up all Exo dependencies properly
- Configured Python environment and packages

### Issue
Despite proper setup, still could not establish successful node-to-node communication in WSL.

**Decision:** Abandoned Windows-based approach entirely

---

## Current Status & Next Steps

### Decision by JB
"Build a cluster from scratch and install whatever we want to make the cluster"

### Planned Approach
**New Strategy:** Fresh Linux installation

**Reasons for Linux Approach:**
1. Exo has proven stability on Linux (prior experience)
2. Better GPU driver support and CUDA compatibility
3. More mature networking stack for distributed computing
4. Eliminate Windows-specific compatibility issues

### Open Questions
- Which Linux distribution to use? (Ubuntu Server, Debian, CentOS, etc.)
- Bare metal or containerized approach? (Docker/Kubernetes?)
- Alternative clustering frameworks to consider? (Ray, Dask, custom solution?)
- Network topology and configuration requirements

---

## Lessons Learned

### Technical Insights
1. **Windows Compatibility:** Exo framework not production-ready for Windows despite modifications
2. **WSL Limitations:** WSL adds complexity for GPU clustering and networking
3. **Firewall Issues:** Network-based clustering requires careful firewall configuration
4. **Dependency Management:** Python-based distributed systems have complex dependency chains

### Process Insights
1. Starting with known-working environment (Linux) would have saved time
2. Need better documentation of exact error messages and logs
3. Should document system specifications and software versions for reproducibility

---


## Timeline Summary

| Phase                            | Duration    | Outcome                             |
| -------------------------------- | ----------- | ----------------------------------- |
| Phase 1: Windows + Exo           | ~1 day      | Failed - dependency issues          |
| Phase 2: First WSL attempt       | ~1 day      | Failed - environment issues         |
| Phase 3: Modified Windows        | ~1 day      | Partial success - cluster connected |
| Phase 4: Model testing           | ~1 day      | Failed - download loop              |
| Phase 5: Second WSL              | ~1 day      | Failed - node connection            |
| **Current:** Fresh Linux install | In planning | TBD                                 |

---


**Document Status:** Work in Progress
**Last Updated:** 2025-11-18
**Updated By:** Mohamed Sameer
