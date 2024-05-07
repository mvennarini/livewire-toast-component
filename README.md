# Documentazione d'Uso


## Posizionamento componente

Assicurati di includere il componente nel layout dell'applicazione utilizzando:

```blade
@livewire('percorso/al/toast-component') //nel file Blade appropriato.
```

## Utilizzo da un componente Livewire

Per dispacciare da un componente Livewire, utilizza il seguente formato nel codice PHP:

```php
$this->dispatch('notifica', [
    'toastData' => [
        'message' => 'Spesa aggiunta con successo!',
        'type' => 'help', // Può essere 'success', 'error', 'warning', 'help', o un altro valore a tua scelta
    ]
]);
```
## Utilizzo lato Javascript

Per dispacciare lato javascript, utilizza il seguente formato di codice Javascript:

```javascript
Livewire.dispatch('notifica', {
    toastData: {
        message: 'Spesa aggiunta con successo!',
        type: 'success' // Può essere 'success', 'error', 'warning', 'help', o un altro valore a tua scelta
    }
});
```

