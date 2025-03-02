# Fundamentals of Web apps

## 0.1: HTML
Review the basics of HTML by reading this tutorial from Mozilla: [HTML tutorial](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics).

## 0.2: CSS
Review the basics of CSS by reading this tutorial from Mozilla: [CSS tutorial](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics).


## 0.3: HTML Forms
Review the basics of HTML Forms by reading this tutorial from Mozilla: [HTML Forms](https://developer.mozilla.org/en-US/docs/Learn/Forms/Your_first_form).

## 0.4 New note diagram
Create a diagram depicting the situation where the user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes by writing something into the text field and clicking the Save button.

![New_note_diagram](https://github.com/user-attachments/assets/d268174a-2beb-49a3-909a-31c2e20666ff)

### mermaid code 0.4
    sequenceDiagram
    participant browser
    participant server

    Note right of browser:  The user types a note into the text field and clicks the Save button.
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note.
    Note right of browser:  The browser sends an HTTP POST request to the server address, the server processes the POST request, creates a new note.
    activate server
    server-->>browser: Status Code: 302 Found
    Note left of server: The server responds with an HTTP status code 302, which is a URL redirect.
    deactivate server

    Note right of browser: This redirect causes the browser to make a new HTTP GET request to the address
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML file
    Note left of server: The server responds with the HTML file.
    deactivate server
    
    Note right of browser: The browser then requests the CSS file
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: Css FIle
    Note left of server: The server sends the CSS file.
    deactivate server
    
    Note right of browser: The browser requests the JavaScript file 
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JS FIle
    Note left of server: The server sends the JavaScript file.
    deactivate server
    
    Note right of browser: The browser executes the JavaScript code, which makes an HTTP GET request to fetch the JSON data containing the notes.
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server-->>browser: {content: 'neden', date: '2024-09-12T11:44:56.604Z'}
    Note left of server: The browser executes an event handler that renders the notes, with the new one created "neden".
    
## 0.5 Single page app diagram
Create a diagram depicting the situation where the user goes to the single-page app version of the notes app at https://studies.cs.helsinki.fi/exampleapp/spa.

![spa_diagram](https://github.com/user-attachments/assets/22a7c0b5-84c4-408c-a847-db711fe2bc67)

### mermaid code 0.5
    sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JS file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: 
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
    
## 0.6 New note in Single page app diagram
Create a diagram depicting the situation where the user creates a new note using the single-page version of the app.

![spa_new_note](https://github.com/user-attachments/assets/449638b5-b18e-40e8-b4dd-3d817751e1a3)

### mermaid code 0.6
    sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user types a note into the text field and clicks the Save button.
    Note right of browser: The browser executes the event handler that prevents the default form submit
    Note right of browser: The browser creates a new note, adds it to the notes list, and rerenders the note list on the page
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of browser: The browser sends the new note as JSON data to the server
    activate server
    server-->>browser: Status Code: 201 Created
    Note left of server: The server responds with status code 201 Created
    deactivate server

    Note right of browser: The browser stays on the same page, and no further HTTP requests are made thanks to single-page architecture
    
    
[![headerlogo](https://github.com/user-attachments/assets/883f6503-3644-4e13-985d-48552dd83ced)](https://fullstackopen.com/en/part0/fundamentals_of_web_apps)

