# Parte 0 — Ejercicio 0.5: diagrama de aplicación de una sola página

```mermaid
sequenceDiagram
    participant navegador
    participant servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate servidor
    servidor-->>navegador: Documento HTML (SPA)
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate servidor
    servidor-->>navegador: Archivo CSS
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate servidor
    servidor-->>navegador: Archivo JavaScript (spa.js)
    deactivate servidor

    Note right of navegador: El navegador empieza a ejecutar spa.js<br/>y obtiene las notas en JSON

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate servidor
    servidor-->>navegador: [{ "content": "...", "date": "..." }, ... ]
    deactivate servidor

    Note right of navegador: El navegador renderiza la lista de notas (DOM)

    Note right of navegador: Al enviar el formulario, JS usa e.preventDefault()<br/>para evitar recargar la página

    navegador->>servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa<br/>(Content-Type: application/json)<br/>{ "content": "...", "date": "..." }
    activate servidor
    servidor-->>navegador: 201 Created
    deactivate servidor

    Note right of navegador: No hay redirección ni recarga<br/>No se envían más solicitudes HTTP
