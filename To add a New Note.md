sequenceDiagram
    participant browser
    participant server

    Note over browser: User writes a note in the text field
    browser->>browser: Capture note input

    Note over browser: User clicks the Save button
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: Server processes the new note
    server-->>browser: Response with success message
    deactivate server

    Note right of browser: The browser updates the UI to show the new note
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated notes data
    deactivate server

    Note right of browser: The browser re-renders the notes list with the new note
