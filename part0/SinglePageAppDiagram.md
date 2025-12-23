```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: User opens SPA version of the notes app

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML (SPA shell)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JavaScript (SPA logic)
    deactivate server

    Note right of browser: Browser executes JS and fetches existing notes as JSON

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON list of notes
    deactivate server

    Note over browser: User types a note and clicks “Save”

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note left of server: Server stores new note
    server-->>browser: HTTP 201 Created
    deactivate server

    Note right of browser: Browser updates UI using JS without page reload
