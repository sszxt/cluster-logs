
Today was a long one, but a productive one. We finally got the direct ethernet connection going, spent time fine-tuning a model, wrestled with some setup issues, and eventually got a distributed LLaMA cluster to actually run. Here’s a clean write-up of everything that happened.

---

## Direct Ethernet Setup

- We hooked up a proper ethernet line between the systems.
- The connection test hit **~1 Gbps**, which is actually solid.
- This connection is now powering the whole distributed and model download workflow.

---

## Model Fine-Tuning & Weight Experiments

- Spent a good chunk of the day fine-tuning a model.
- Also tried playing around with the weights and various configurations.
- Everything went well overall.
- Meanwhile, Ismaiel was working on his app… and yeah, he’s pretty fed up with it.

---

## HuggingFace Model Download Issues

- Even with the fresh ethernet line, **HuggingFace model downloads via Exo were still acting weird**.
- Models try to download but get stuck or restart — still not sure why.
- Need to troubleshoot this later (authentication? caching? firewall? mirrors?).

---

## Distributed LLaMA Setup

- Installed the distributed llama setup.
- The first run threw some **IP-related issues**, but those got resolved.
- The server endpoint is running locally at:
	- **[http://127.0.0.1](http://127.0.0.1/)**

- Worker nodes need to be assigned **their actual machine IPs** in the command.
- After updating all that, everything finally worked.

---

## Cluster Creation

- Successfully created a cluster.
- Nodes are talking to each other.
- Haven’t benchmarked it yet, but **things are alive**.

---

## GPU vs CPU

- Right now, the model seems to be running on the **CPU**.
- To move it to GPU, the model probably needs to be **recompiled** with the correct backends.
- We’ll figure that part out later.

---
Overall: a very productive day. Ethernet sorted, LLaMA distributed cluster up, IP issues resolved, fine-tuning done, and a clear idea of what’s next — GPU configuration + fixing the HuggingFace download problem.

More to update once we run benchmarks and fully move workloads to the GPUs.


**Document Status:** Work in Progress
**Last Updated:** 2025-11-21
**Updated By:** Mohamed Sameer