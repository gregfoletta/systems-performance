---
title: "Chapter 3 - Operating Systems"
---

# Background

Kernel manages CPU scheduling, memory, filesystems, network protocols, and system devices (disks, network interfaces, etc). It provides access to devices and kernel services built upon them via system calls.

System libraries are often used to provide richer and easier programming interface than the system calls alone.

## Kernel Execution

The kernel is a large program that executes on demand either from a system call or an interrupt. There are some lightweight kernel threads that run asynchronously.

Workloads that perform frequent I/O will spend a significant amount of time executing in the kernel context. Workloads that are compute intensive will spend most of their time in user context, however they are still affected by the kernel. The most obsvious way is the way the kernel schedules the workloads (and other workloads) on to the CPUs available.

## Clock

A core component of the original UNIX kernel is the `clock()` routing, executed from a timer interrupt. It has historically been executed 60, 100 or 1,000 times per second, and each executiom is called a 'tick'.

Its functions have included updating system time, expiring timers and time slices for thread scheduling, maintaining CPU stats, and executing *callouts* (scheduled kernel routines).

There have been performance issues with the clock, improved in later kernels:

* **Tick Latency**: for 100Hz clocks, 10ms of latency may be encountered for a timer as it waits to be processes on the next tick.
* **Tick Overhead**: modern processers have dynamic power features which allow them to idle during periods of low use. The clock routing interrupts this process. Linux has implemented *dynamic ticks* so that the timer routing does not fire when the system is idle.

Modern kernels have moved functionality out of the clock routine to on-demand interrupts.

## Kernel Mode

The kernel is the only program running in a special CPU mode called *kernel mode*. User processes run in *user mode*. Execution *context-switches* between the modes.

Each mode has its own execution context, including stack and registers. The context switch takes CPU cycles which adds a small amount of overhead for each I/O.

# Stacks




