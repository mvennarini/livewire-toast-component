# Documentazione d'Uso


## Posizionamento componente

Assicurati di includere il componente nel layout dell'applicazione utilizzando:

```blade
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <meta name="csrf-token" content="{{ csrf_token() }}">

        <title>{{ config('app.name', 'Laravel') }}</title>

        <!-- Fonts -->
        <link rel="preconnect" href="https://fonts.bunny.net">
        <link href="https://fonts.bunny.net/css?family=figtree:400,500,600&display=swap" rel="stylesheet" />

        <!-- Scripts -->
        @vite(['resources/css/app.css', 'resources/js/app.js'])

        <!-- Styles -->
        @livewireStyles
    </head>
    <body class="font-sans antialiased">
        <x-banner />

        <div class="min-h-screen bg-gray-100">
            @livewire('navigation-menu')

            <!-- Page Heading -->
            @if (isset($header))
                <header class="bg-white shadow">
                    <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                        {{ $header }}
                    </div>
                </header>
            @endif

            <!-- Page Content -->
            <main>
                {{ $slot }}
            </main>
        </div>

        @stack('modals')

        @livewireScripts
        @livewire('percorso/al/toast-component') //nel file Blade appropriato.
    </body>
</html>
```

## Utilizzo da un componente Livewire

Per dispacciare da un componente Livewire, utilizza il seguente formato nel codice PHP:

```php
// Può essere 'success', 'error', 'warning', 'help'
$this->dispatch(
    'notifica',
        toastData: [
        'message' => 'Messaggio di successo!',
        'type' => 'success',
    ]
);


$this->dispatch(
    'notifica',
        toastData: [
        'message' => 'Messaggio di errore :(',
        'type' => 'error',
    ]
);

$this->dispatch(
    'notifica',
        toastData: [
        'message' => 'Messaggio di Warning!',
        'type' => 'warning',
    ]
);

$this->dispatch(
    'notifica',
        toastData: [
        'message' => 'Messaggio di aiuto!',
        'type' => 'help',
    ]
);
```
## Utilizzo lato Javascript

Per dispacciare lato javascript, utilizza il seguente formato di codice Javascript:

```javascript
// Può essere 'success', 'error', 'warning', 'help'
Livewire.dispatch('notifica', {
    toastData: {
        message: 'Messaggio di successo',
        type: 'success'
    }
});

Livewire.dispatch('notifica', {
    toastData: {
        message: 'Messaggio di errore',
        type: 'error'
    }
});

Livewire.dispatch('notifica', {
    toastData: {
        message: 'Messaggio di warning',
        type: 'warning'
    }
});

Livewire.dispatch('notifica', {
    toastData: {
        message: 'Messaggio di aiuto',
        type: 'help'
    }
});
```

