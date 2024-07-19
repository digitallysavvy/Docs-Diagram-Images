# Sequence Diagram

```mermaid
sequenceDiagram
    participant Host as HOST with Agora Video SDK
    participant Agora as Agora SD-RTN&trade;
    participant Audience as AUDIENCE with Agora Video SDK

    Host ->> Agora: Join a Channel 
    Host ->> Agora: Publish Stream
    Audience ->> Agora: Join a Channel
    Audience ->> Agora: Subscribe to a Stream 
    Agora ->> Host: Subscribe to a Stream
    Agora ->> Audience: Publish Stream
```
