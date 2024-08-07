# Sequence Diagram

```mermaid
flowchart LR
  subgraph "UID 1"
    joinChannel --> onJoinChannelSuccess --> onConnectionStateChanged1
  end

  subgraph "UID 2"
    onUserJoined --> onUserOffline
  end

  onJoinChannelSuccess --> T1
  T1 --> onConnectionStateChanged2
  onConnectionStateChanged1 --> T2
  T2 --> onConnectionStateChanged3
  onConnectionStateChanged2 --> T3
  onConnectionStateChanged3 --> T4
  T3 --> onConnectionLost --> reconnection["SDK automatically reconnects"]
  T4 --> onConnectionStateChanged4
  reconnection -.-> onConnectionStateChanged4
  onConnectionStateChanged4 --> T7

  T0["T0"]
  T1["T1"]
  T2["T2"]
  T3["T3"]
  T4["T4"]
  T5["T5"]
  T6["T6"]
  T7["T7"]
```
