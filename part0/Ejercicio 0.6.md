sequenceDiagram
    actor U as Usuario
    participant N as Navegador
    participant S as Servidor

    U->>N: Escribe una nota y pulsa "Save"
    Note right of N: JS captura el submit y ejecuta e.preventDefault()

    Note right of N: JS crea el objeto note<br/>notes.push(note) y re-renderiza la lista (DOM)

    N->>S: POST /new_note_spa (application/json)\n{ content: "...", date: "..." }
    activate S
    S-->>N: 201 Created
    deactivate S

    Note right of N: No hay redirect ni recarga<br/>No se hacen más requests HTTP
