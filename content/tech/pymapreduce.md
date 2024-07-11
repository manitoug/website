---
title: Pymapreduce
linkTitle: Implementing Map Reduce in Python
date: 2024-06-28T16:20:48+02:00
draft: true
---

## What is Map Reduce ?

MapReduce is a way to do multi-processing on different machines in an organization. The protocol is a corner stone of the modern distributed computing frameworks, such as Apache Spark.

Commonly used in datacenters for Big Data applications, its principles doesn't limit to these professional infrastructures and can be applied on every consumer tier computers for ann in house, cheap alternative datacenter alternative.

## Project goals

This project objective is to code a basic, pure python, implementation of the Map Reduce protocol for a fixed, wordcount program.
Given a plain text file containing an arbitrary text, the overall program deployment is:

1. To split and distribute data files to a cluster of consumer hardware on the local network.
   (N.B; In a real environment, a distributed DB, at the closest possible distance of the computing units, should be used to avoid congestion on the network)
2. Distribute the program to be launched on the machines.
3. Launch the program remotely
4. Aggregate the results and serve the answer.

## Course of Action

The program structure consists of a main file on the host computer controling the global workflow through a simple task list

![fig. 1: supervision program](/images/supervision.png "Supervision Program")

In case of failures, the different programs send back the error to the main program.
