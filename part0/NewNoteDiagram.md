```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: The user types a note and clicks the ‘Save’ button.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note left of server: The server saves new note data
    server-->>browser: HTTP status code 302 (URL Redirect to /notes)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: Document HTML
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: File CSS
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: File JavaScript
    deactivate server

    Note right of browser: The browser executes JS to retrieve the latest JSON

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "new note", "date": "2025-..." }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback to render all notes, including the new one.
