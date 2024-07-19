# Sequence Diagram

```mermaid
sequenceDiagram
    participant Token_server as Token server <br/>Implemented by you
    participant App as App <br/>Implemented by you
    participant SD_RTN as SD-RTN <br/>Provided by Agora

    %% Interaction: Join a channel with authentication
    App->>+Token_server: Request Token<br/>(channel name, role, token type, user ID)
    Token_server-->>-App: Validate user against internal security
    Token_movies-->>-App: Generate and return token
    App->>SD_RTN: Join channel with uid, channel name, token
    SD_RTN->>App: Validate token
    App-->>App: Trigger callback after adding user to channel

    %% Interaction: Token Privilege Will Expire
    App->>+Token_server: Request fresh token<br/>(channel name, role, token type, user ID)
    Token_server-->>-App: Validate user request against internal logic
    Token_server-->>-App: Generate and return fresh token
    App->>SD_RTN: RenewToken with fresh token
```
