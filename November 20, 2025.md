Today we installed Ubuntu on both systems and set up Exo. The installations went smoothly, and the hardware detection seems stable. However, we are still facing an issue where the model keeps downloading repeatedly. This needs further investigation. One possible direction is testing with a direct Ethernet connection to rule out any network inconsistencies.

## Current Challenges

- **Model Redownloading Issue:**  
    Exo repeatedly downloads the model instead of using a cached copy. We still need to diagnose whether this is due to network configuration, permissions, or some missing cache directory. Testing with a direct Ethernet link might help us isolate the problem.

- **GPU Availability:**  
    Most of the GPUs available right now are AMD. Since AMD isn’t suitable for our intended workload, they don’t help much for Exo or model acceleration. We need more compatible GPUs (likely NVIDIA) for proper execution.

- **Missing Hardware Components:**  
    We still need additional motherboards and other supporting components to complete the build and scale up.

## Next Steps

1. Try running Exo with a direct Ethernet connection between systems to see if the model download issue is network-related.
2. Source compatible GPUs and necessary hardware (motherboards, etc.).
3. Once Exo works reliably across the network, install and run it on all connected PCs so they can operate in the background as part of a distributed setup.

---
**Document Status:** Work in Progress
**Last Updated:** 2025-11-20
**Updated By:** Mohamed Sameer