# Parte 0 — Ejercicio 0.4: Nuevo diagrama de nota

```mermaid
sequenceDiagram
    autonumber
    actor U as Usuario
    participant B as Navegador
    participant S as Servidor

    U->>B: Clic en botón "Guardar" (submit formulario)
    B->>S: POST /new_note (body: note=texto_ingresado)

    activate S
    S->>S: notes.push({ content: req.body.note, date: new Date() })
    S-->>B: 302 Redirect (Location: /notes)
    deactivate S

    B->>S: GET /notes
    S-->>B: 200 OK (HTML página de notas)

    B->>S: GET /main.css
    S-->>B: 200 OK (CSS)

    B->>S: GET /main.js
    S-->>B: 200 OK (JS)

    B->>S: GET /data.json
    S-->>B: 200 OK (JSON con notas)

    Note over B: Renderiza la página y muestra la lista de notas actualizada
