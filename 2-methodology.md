---
title: "Chapter 2 - Methodology"
---

# Modeling

Analytical modeling can be used for scalabilty analysis: how performance scales as load or resources scale. It can be considered a third type of performance evaluation activity along with observability (measurement) and experimental testing (simulation).

Performance is best understood when at least two of these activities are performed.


## Visual Identification

When enough results are collectted experimentally, plotting performance against the scaling parameter may reveal a pattern. Some scalability profiles to look for:

* Linear: performance increases proportionally as the resource is scaled. May not continue for ever and may be the early stages of another pattern.
* Contention: some components of the architecture are shared and can only be used serially. Performance starts to drop off as these shared resources begin to reduce the effectiveness of scaling
* Coherence: the tax to main data conherency - including propagation of changes - begins to outweight the benefits of scaling. The performance starts drops away and then starts to get worse as the resource is scaled.
* Knee point: a factor is encountered at a scalability point that changes the scalability profile. The performance levels off immediately.
* Scalability ceiling: a hard limit is reached and performance flatlines. This may be a device bottleneck or a software imposed limit.

## Amdahl's Law of Scalability

This law models system scalability, accounting for serial components of workloads that do not scale in parallel.

$$ C(N) = \frac{N}{1    
