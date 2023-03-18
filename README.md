# fullstackopen-part0-exercises

## Exercise 0.4
The user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes by writing something into the text field and clicking the submit button.

The sequence of events that occurs is depicted below.

```mermaid
sequenceDiagram
    participant client
    participant server
    
    
    client->>server: POST 302 https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>client: input value is saved to the data
    deactivate server
    
    
    client->>server: GET 304 https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>client: new note appears at the bottom of the list
    deactivate server
    
    
    client->>server: GET 304 https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>client: GET 304 https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server
    
    client->>server: 2. submit button clicked 
    client->>server: 3. form performs action be using POST method to /new_note directory (address)
    server-->>client: 4. the note is added to the page
    Note over server, client: and redirects the user back to the /notes address with the updated entry included
    server-->>client: 5. GET css styling of /notes address
    server-->>client: 6. GET javascript of /notes address
    server-->>client: 7. GET json data of /notes address
```
