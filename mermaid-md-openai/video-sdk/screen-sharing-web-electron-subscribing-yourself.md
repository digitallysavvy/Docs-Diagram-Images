# Sequence Diagram

```mermaid
sequenceDiagram
    participant Sender
    participant Subscriber

    rect rgb(255,255,255)
        note right of Sender: Sender
        participant Client_A as Client A
        participant Client_B as Client B
    end
    
    rect rgb(255,255,255)
        note right of Subscriber: Subscriber
        participant Client_C as Client C
    end

    Client_A ->> Client_B: Audio &amp; Video track
    Client_B ->> Client_C: Audio &amp; Video track
    Client_A -) Client_C: Screen Sharing Track

    note left of Client_B: Note: To avoid additional costs, do not subscribe to a local screen sharing track.
```
