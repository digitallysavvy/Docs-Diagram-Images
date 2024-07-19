# Sequence Diagram

```mermaid
sequenceDiagram
    participant User
    participant App
    participant Developer's Authentication System
    participant API

    User->>App: Start the app
    User->>App: Select a channel to join

    subgraph Media stream encryption
        App->>Developer's Authentication System: Initiate the Video SDK engine
        App->>Developer's Authentication System: Request a 32-byte key
        App->>Developer's Authentication System: Request a 32-byte salt in Base64 format

        Developer's Authentication System->>API: Generate a 32-byte string using OpenSSL for keys and salts
        API->>Developer's Authentication System: Generated string for key
        Developer's Authentication System->>App: Requested key

        Developer's Authentication System->>API: Generate a 32-byte string in Base64 format using OpenSSL for salts
        API->>Developer's Authentication System: Generated string for salt
        Developer's Authentication System->>App: Requestewd salt

        App->>App: Create a encryption configuration using the received salt and key
        App->>App: Call the method to set the encryption configuration
    end

    App->>App: Join a channel with user Id, channel name, and token
    App->>App: Join accepted
```
