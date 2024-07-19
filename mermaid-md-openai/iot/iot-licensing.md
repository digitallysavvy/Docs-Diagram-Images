# Sequence Diagram

```mermaid
sequenceDiagram
    participant You
    participant IoT_SDK as IoT SDK
    participant Agora_Sales as Agora Sales
    participant REST_API as REST API

    You->>Agora_Sales: Contact Agora sales to request a license
    Agora_Sales->>You: Send license information
    You->>IoT_SDK: Activate the license
    IoT_SDK->>Agora_Sales: Send activation info
    Agora_Sales->>REST_API: Activate the license
    You->>IoT_SDK: Write a license to the device
```
