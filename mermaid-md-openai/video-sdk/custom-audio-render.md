# Sequence Diagram

```mermaid
sequenceDiagram
    participant App as App [&lt;square&gt;]
    participant SDK as SDK [&lt;square&gt;]
    participant Agora as Agora SD-RTN [&lt;cloud&gt;]
    
    App->>+SDK: Create and initialize the engine
    SDK-->>-App: Acknowledge
    App->>+SDK: Turn on custom audio rendering
    SDK-->>-App: Acknowledge

    subgraph Custom audio rendering
        App->>+SDK: Join a channel
        SDK->>+Agora: Request to join the channel
        Agora-->>-SDK: Confirm channel joined
        SDK-->>-App: Confirm channel joined

        App->>+SDK: Pull remote audio data
        SDK->>+Agora: Request remote audio data
        Agora-->>-SDK: Send remote audio data
        SDK-->>-App: Deliver remote audio data
        
        App->>+SDK: Leave the channel
        SDK->>+Agora: Request to leave the channel
        Agora-->>-SDK: Confirm channel left
        SDK-->>-App: Confirm channel left
    end
    
    App->>+SDK: Destroy the engine
    SDK-->>-App: AcknowledgeDestroy
```
