# Object Storage basic commands, tutorial

Last updated: 22.10.2026

## General Information

The new Object Storage server that is currently being implemented, is a type of sever that uses a different protocol to what we've been using so far: it is not a Linux server, but an Object Storage (S3) File System that only allows communication through the AWS CLI tool. I will try to explain this better along the tutorial. It is a new concept for me too, so I plan to update this tutorial with everything I learn and discover, as to make your experience with it as painless as I can make it be.

## Objective

The Object Storage is intended to be an archive of data for inputs and ouputs. It is intended to communicate with anthill4.0 which will be used as the computational power. So the idea is the following:

```mermaid
{
  "theme": "redux-color",
  "look": "handDrawn"
};
flowchart LR;
    subgraph WetLab[WetLab];
        Gate1{Do I want to analyse some data?} --> |Yes| Illumina[First obtain Illumina raw file];
    end;
    
    subgraph anthill4[anthill4.0];
        fasta[Generate fasta files];
        pipeline[Start pipeline] --> Intermediate[Intermediate files];
        Intermediate --> Output[Output files];
        Intermediate --> Delete;
        Output --> Gate3{Will you need for future analysis?};
        Gate3 --> |No| Delete[Delete];
        Gate4{By future you mean right away?};
        Gate3 --> |Yes| Gate4;
        Gate4 --> |Yes| pipeline;

    end;

    Illumina --> fasta;
    
    subgraph Storage[Object storage];
        stored[Stored files] --> Gate2{Read-only};
    end;
    
    fasta --> stored;
    Illumina --> stored;
    Gate2--> pipeline[Start pipeline];
    Gate4 --> |No, most likely in months| stored;
``` 
