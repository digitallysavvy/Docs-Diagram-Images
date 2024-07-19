# Sequence Diagram

```mermaid
sequenceDiagram
    participant g as getScreenCaptureSources
    participant d as startScreenCaptureByDisplayId
    participant w as startScreenCaptureByWindowId
    participant j as joinChannelEx<br />(publishScreenTrack: true)
    participant a as Agora SD-RTN&#x2122;

    g ->>+ d: displayId
    g ->>+ w: window="&#x2073;"
    d ->>+ j
    w ->> j
    j ->> a
```
