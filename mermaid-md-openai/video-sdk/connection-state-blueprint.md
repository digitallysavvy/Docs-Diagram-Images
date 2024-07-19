# Sequence Diagram

```mermaid
flowchart LR
    JoinChannel --> |T0| FOJoinChannelSuccess
    JoinChannel --> |T0| FOOnConnectionStateChanged

    subgraph T0 [T0]
    end
    subgraph T1 [T1]
    end
    subgraph T2 [T2]
    end
    subgraph T3 [T3]
    end
    subgraph T4 [T4]
    end
    subgraph T5 [T5]
    end
    subgraph T6 [T6]
    end
    subgraph T7 [T7]
    end

    T0 --> T1 --> T2 --> T3 --> T4 --> |Dashed| SDKAutomaticallyReconnects
    T5 --> T6 --> T7

    subgraph SDKAutomaticallyReconnects [SDK automatically reconnects]
    end

    FOOnConnectionStateChanged -->|CONNECTION_STATE_CONNECTED, CONNECTION_CHANGED_JOIN_SUCCESS&#10;Network connection successful| T1
    FOOnConnectionStateChanged -.->|CONNECTION_STATE_RECONNECTING, CONNECTION_CHANGED_INTERRUPTED&#10;Re-establishing Network connection| T3
    FOOnConnectionLinkedList -.->|CONNECTION_STATE_RECONNECTING, CONNECTION_CHANGED_LOST&#10;Network connection interrupted| T4
    FOOnConnectionStateChanged -.->|CONNECTION_STATE_FAILED, CONNECTION_CHANGED_JOIN_FAILED&#10;Network connection failed| T7

    FOOnUserJoined -.- |FOOnUserJoined&#10;Remote user comes online| T2
    FOOnUserOffline -.- |FOOnUserOffline (reason USER_OFFLOYEE_DROPPED)&#10;Remote user is offline| T6
```
