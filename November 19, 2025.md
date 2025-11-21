## **1. Windows Environment Limitations**

During the setup and testing process, we identified that the Windows environment is not suitable for the software stack we are working with. Most of the required tools, including the components used by Exo and other related dependencies, are designed primarily for Linux systems.  
Because of this:

- Several required packages are not supported on Windows.
- Some tools fail to install or run correctly due to missing Linux-only dependencies.
- The overall workflow becomes unstable because the software expects a native Linux environment.

## **2. Python Version Compatibility Issues**

Another major issue we found is that the system only works reliably with **Python 3.12**.  
The reasons behind this include:

- Dependencies used by the Exo software currently only support Python 3.12.
- Other Python versions either fail to install the required packages or break due to dependency conflicts.
- This restriction makes the environment more fragile and harder to maintain across machines.

## **3. WSL Networking and Protocol Access Problems**

Even though WSL provides a Linux-like environment, we observed that it cannot fully integrate with the network protocols we configured on Windows.  
Specifically:

- WSL is unable to access certain Windows-level protocol configurations.
- Windows Firewall and other system-level network security features are blocking the communication flows we set up.
- Some of the routing, port forwarding, and protocol operations that work on native Linux fail inside WSL due to these restrictions.

This is causing disruptions in the setup and prevents the system from functioning as expected.

## **4. Network Setup Concerns**

We also identified a limitation with the current direct or Windows-managed networking setup.  
There is a doubt that connecting systems using a **proper network switch** and **cross-over Ethernet cables** might be a more reliable approach.  
This would provide:

- A cleaner, isolated network environment
- Direct communication between machines without interference from Windows routing
- Better stability for whatever distributed workflows we are running

## **5. GPU Hardware Situation**

Right now, the available hardware includes:

- Multiple **GTX 1450** GPUs
- Some **RTX 2070** GPUs

The challenge here is that:

- These GPUs are not very strong by today’s standards.
- VRAM is limited, which restricts the kind of workloads we can run.
- It is unclear how effectively these GPUs can support the tasks we need, especially if the workloads are compute-heavy or require modern GPU capabilities.

## **6. Need for Additional Hardware Support**

Based on the issues above, it’s clear that we need additional support on the hardware side.  
This may include:

- More compatible GPUs
- A stable Linux-based system
- Better networking infrastructure
- And potentially other supporting hardware to ensure everything runs smoothly

---
**Document Status:** Work in Progress
**Last Updated:** 2025-11-19
**Updated By:** Mohamed Sameer
