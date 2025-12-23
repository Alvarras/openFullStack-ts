```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: User writes a new note and clicks "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note left of server: Server saves the new note
    server-->>browser: HTTP 201 Created (JSON response)
    deactivate server

    Note right of browser: Browser updates the notes list using JavaScript(no page reload)
