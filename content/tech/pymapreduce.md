---
title: Pymapreduce
linkTitle: Implementing Map Reduce in Python
date: 2024-06-28T16:20:48+02:00
draft: true
---

## What is Map Reduce ?

MapReduce is a programming model and processing technique designed to handle large-scale data across distributed computing environments. It was introduced to efficiently process vast amounts of data by dividing the workload into manageable chunks. The protocol operates in two main phases:
The "Map" phase, where input data is split into smaller sub-problems and processed independently by different nodes, and the "Reduce" phase, where the results from the Map phase are aggregated and combined to produce the final output. This method leverages the parallel processing capabilities of distributed systems, improving scalability and fault tolerance.

By abstracting the complexity of parallel computation, MapReduce allows developers to focus on writing the core logic for data processing while the underlying framework handles the distribution, synchronization, and fault recovery tasks. The protocol is a corner stone of the modern distributed computing frameworks, such as Apache Spark.

Commonly used in datacenters for Big Data applications, its principles doesn't limit to these professional infrastructures and can be applied on every consumer tier computers for an in-house, cheap datacenter alternative.

## Project goals

This project objective is to code a basic, pure python, implementation of the core features of the Map Reduce protocol for a fixed, wordcount program.
Given a plain text file containing an arbitrary text, the overall program deployment is:

1. To split and distribute data files to a cluster of consumer hardware on the local network.
   (N.B; In a real environment, a distributed DB, at the closest possible distance of the computing units, should be used to avoid congestion on the network)
2. Distribute the program to be launched on the machines.
3. Launch the program remotely
4. Aggregate the results and serve the answer.

## Course of Action

The following figure illustrates the supervision program for our Python implementation of the MapReduce process, specifically focusing on the role of the master node (PC Maître) which orchestrates the overall execution. The supervision program, named master.py, is divided into several key components and stages/

The program structure consists of a main file on the host computer coordinating the cleaning, deployment, and execution of tasks across the distributed machines:

![fig. 1: supervision program](/images/supervision.png "Supervision Program")

In case of failures, the different programs send back the error to the main program.
