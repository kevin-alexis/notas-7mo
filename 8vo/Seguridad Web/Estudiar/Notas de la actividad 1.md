
```ts
// watch es para que este checando si hay cambios en la variable y asi ejecute lo de adentro
watch(notesList, (newNotesList) => {
    localStorage.setItem('notes', JSON.stringify(newNotesList))
  },

  {deep: true} // deep es para que watch vue detecte cambios cuando se modifican los elementos internos de un array u objeto

  // , puesto que es un array, no los detectaria de forma correcta,

  // solo si fuera una reasignación completa
```