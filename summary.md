```mermaid
sequenceDiagram
    autonumber
    loop Every minute
      Cronjob->>Mainframe: Here are the new releases
    end
```

```mermaid
sequenceDiagram
    autonumber
    Client->>Mainframe: I need a job
    Mainframe->>Client: Here is a job
    Client->>Mainframe: Here are the results for this job
```

```mermaid
sequenceDiagram
    autonumber
    Alessia->>Mainframe: What are the recent malicious distributions?
    Mainframe->>Alessia: Here are the latest malicious distributions
    Alessia->>dragonfly-alerts: PING!
```

```mermaid
sequenceDiagram
    autonumber
    actor User
    User->>Alessia: This package is malicious!
    Alessia->>Mainframe: This package is malicious!
    actor PyPI
    Mainframe->>PyPI: This package is malicious!
```
