# Parte 0 — Ejercicio 0.6: Nueva nota en diagrama de aplicación de una sola página

```mermaid
sequenceDiagram
    actor U as Usuario
    participant N as Navegador
    participant S as Servidor

    U->>N: Escribe una nota y pulsa "Save"
    Note right of N: JavaScript intercepta el submit\ny ejecuta e.preventDefault() para evitar recargar la página

    Note right of N: JavaScript crea la nueva nota y la agrega al arreglo\nnotes.push(note) y actualiza la lista en pantalla (DOM)

    N->>S: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa\nContent-Type: application/json\n{ "content": "...", "date": "..." }
    activate S
    S-->>N: 201 Created
    deactivate S

    Note right of N: No hay redirección ni recarga\nNo se hacen más solicitudes HTTP
