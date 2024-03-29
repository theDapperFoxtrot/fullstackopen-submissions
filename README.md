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
    server-->>client: JavaScript is loaded
    deactivate server
    
    client->>server: GET 200 https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>client: json array of objects is retrieved and populates the page
    deactivate server
```
This app will reload the page for every submission.

## Exercise 0.5
The user navigates to the page https://studies.cs.helsinki.fi/exampleapp/spa by following an anchor or entering the URL.

The sequence of events that occurs is depicted below.

```mermaid
sequenceDiagram
    participant client
    participant server
    
    
    client->>server: GET 200 https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>client: HTML document loaded
    deactivate server
    
    
    client->>server: GET 304 https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>client: CSS document loaded
    deactivate server
    
    
    client->>server: GET 200 https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>client: JavaScript is loaded
    deactivate server
    
    client->>server: GET 200 https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>client: json array of objects is retrieved and populates the page
    deactivate server
```
This app will render submissions without the need to reload the page.

## Exercise 0.6
The user creates a new note using the single-page version of the app. https://studies.cs.helsinki.fi/exampleapp/spa

The sequence of events that occurs is depicted below.

```mermaid
sequenceDiagram
    participant client
    participant server
    
    
    client->>server: POST 201 https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>client: render note, add data to json file
    deactivate server
```
The SPA can take the input and render it to the page without the need to reload, while also committing the data to the json file.
