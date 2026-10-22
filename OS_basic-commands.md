# Object Storage basic commands, tutorial

Last updated: 22.10.2026

## General Information

The new Object Storage server that is currently being implemented, is a type of sever that uses a different protocol to what we've been using so far: it is not a Linux server, but an Object Storage (S3) File System that only allows communication through the AWS CLI tool. I will try to explain this better along the tutorial. It is a new concept for me too, so I plan to update this tutorial with everything I learn and discover, as to make your experience with it as painless as I can make it be.

## Objective

The Object Storage is intended to be an archive of data for inputs and ouputs. It is intended to communicate with anthill4.0 which will be used as the computational power. So the idea is the following:

```mermaid
---
config:
  theme: neutral
---
sequenceDiagram
    participant Object Storage
    participant Anthill4.0
    
    Object Storage->>Anthill4.0: Hey man, take this input, and analyze it.
    Anthill4.0-->>Object Storage: Ok, I analysed it. I am saving some temporary files in memory. You want them?
    Note right of Object Storage: No, thank you. I am only meant to store final outputs.
```
