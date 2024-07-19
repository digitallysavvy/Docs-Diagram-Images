# Sequence Diagram

```mermaid
sequenceDiagram
    participant User
    participant Your_app as Your app
    participant Agora
    box "Your app"
        participant Video_SDK as Video SDK
    end
    box "Agora"
        participant SD_RTN as SD-RTN
    end
    rect rgb(240, 240, 240)
        note right of User: Open app
        User ->>+ Your_app: Launch app
        Your_app ->>+ Video_SDK: Initialize engine
        Video_SDK ->>- Your_app: agoraEngine = createAgoraRtcEngine()
        Your_app ->>+ Video_SDK: Enable video
        Video_SDK ->>- Your_app: agoraEngine.enableVideo()
        Your_app ->>+ Video_SDK: Setup video view
        Video_SDK ->>- Your_app: Setup AgoraVideoView
        Your_app ->> Video_SDK: Set client role and profile
        Video_SDK -->>- Your_app: Settings applied
        Your_app ->>+ Agora: Request token
        Agora ->>- Your_app: Token
        Your_app ->>+ Video_SDK: Join channel
        Video_SDK -->>- Your_app: Joined channel
        Your_app ->> Video_SDK: Start local preview
        Video_SDK -->>- Your_app: Preview started
        Your_app ->> Video_SDK: Wait for remote user
        Video_SDK ->>- Your_app: onUserJoined
        Your_app ->> SD_RTN: Send data streams
        SD_RTN ->> Your_app: Display remote video
    end
    rect rgb(245, 245, 245)
        note right of User: Close app
        User ->>+ Your_app: Close app
        Your_app ->>+ Video_SDK: Leave channel
        Video_SDK -->>- Your_app: Channel left
        Your_app ->>- User: App closed
    end
```
