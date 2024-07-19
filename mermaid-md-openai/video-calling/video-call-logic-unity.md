# Sequence Diagram

```mermaid
sequenceDiagram
    participant User as <br />User
    participant Video_SDK as Video SDK
    participant SD_RTN as SD-RTN

    subgraph Opening the Game
        User->>+Video_SDK: Open game
        Video_SDK->>-Video_SDK: agoraEngine=IRtcEngine.GetEngine()
    end

    subgraph Starting the Call
        User->>+Video_SDK: Start call
        Video_SDK->>+SD_RTN: agoraEngine.JoinChannelByKey()
        SD_RTN-->>-Video_SDK: Acknowledge
    end

    subgraph Joining the Call
        User->>+Video_SDK: Join call
        Video_SDK->>Video_SDK: OnUserJoined()
        Video_SDK->>+Video_SDK: agoraEngine.EnableVideo()
        Video_SDK->>+Video_SDK: agoraEngine.EnableVideoObserver()
    end

    subgraph During Call
        User->>+Video_SDK: Receive and send data stream
        Video_SDK->>+SD_RTN: Stream data
    end

    subgraph Leaving the Call
        User->>+Video_SDK: Leave call
        Video_SDK->>+SD_RTN: agoraEngine.leaveChannel()
        SD_RTN-->>-Video_SDK: Acknowledge
    end

    subgraph Closing the Game 
        User->>+Video_SDK: Close game
        Video_SDK->>Video_SDK: agoraEngine.destroy()
        User-->>-User: End
    end
```
