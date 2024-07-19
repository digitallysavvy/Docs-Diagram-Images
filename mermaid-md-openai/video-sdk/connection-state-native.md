# Sequence Diagram

```mermaid
flowchart LR
    subgraph "Join Channel Process"
        joinChannel(Join channel) --> onJoinChannelSuccess(Joined the channel successfully)
        onJoinChannelSuccess --> T0{{"T0"}}
        T0 --> onConnectionStateChanged1[(connection_state_connected, connection_changed_join_success):<br>Network connection successful]
        onConnectionStateChanged1 --> onUserJoined(onUserJoined)

        T0 -->|dashed| T1{{"T1"}}
        T1 --> onConnectionStateChanged2[(connection_state_reconnecting, connection_changed_interrupted):<br>Re-establishing Network connection]
        T1 -->|dashed| T2{{"T2"}}
        T2 --> onConnectionStateChanged3[(connection_state_reconnecting, connection_changed_lost):<br>Network connection interrupted]
        
        T1 -->|dashed| T3{{"T3"}}
        T3 -.-> SDK[("SDK automatically reconnects")]
        T3 --> onConnectionStateChanged4[(connection_state_failed, connection_changed_join_failed):<br>Network connection failed]
        
        T2 -->|dashed| T4{{"T4"}}
        T3 -->|dashed| T5{{"T5"}}
    end
    onUserJoined --> UID1(UID 1) --> UID2(UID 2)
    T5 --> onUserOffline(onUserOffline (reason dropped): <br>Remote user is offline)

    classDef dashedLine stroke-dasharray: 5 5;
    linkStyle 4,6,8,10,12 class dashedLine
```
