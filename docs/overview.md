# Overview

Dragonfly consists of a few main components: the mainframe, the cronjob, the client, and the Discord bot.

## Components

### Cronjob

The cronjob is responsible for periodically checking PyPI for new releases and sending them to the mainframe to stage for analysis.
The Mainframe is responsible for making sure that it doesn't process the same release twice.

```mermaid
sequenceDiagram
    autonumber
    loop Every minute
      Cronjob->>Mainframe: Here are the new releases
    end
```

### Clients

Clients request a job (a package to scan) from the Mainframe, analyze the package, and send the results back to the Mainframe.

```mermaid
sequenceDiagram
    autonumber
    Client->>Mainframe: I need a job
    Mainframe->>Client: Here is a job
    Client->>Mainframe: Here are the results for this job
```

### Discord bot

Every few minutes, the Discord bot will request the latest malicious distributions from the Mainframe and post them to the #dragonfly-alerts channel.

```mermaid
sequenceDiagram
    autonumber
    Bot->>Mainframe: What are the recent malicious distributions?
    Mainframe->>Bot: Here are the latest malicious distributions!
    Bot->>dragonfly-alerts: PING!
```

### User confirmation and reporting

The bot creates an embed in the #dragonfly-alerts channel for each malicious package.
Users can click the "report" button to confirm that the package is malicious, and report it to PyPI.

```mermaid
sequenceDiagram
    autonumber
    actor User
    User->>Bot: This package is malicious!
    Bot->>Mainframe: This package is malicious!
    actor PyPI
    Mainframe->>PyPI: This package is malicious!
```
