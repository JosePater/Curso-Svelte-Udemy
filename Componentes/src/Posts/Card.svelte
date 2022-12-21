<script>
    import {createEventDispatcher} from 'svelte' // Librería Svelte para evento
    const dispatch = createEventDispatcher();
    // Variables para exportar
    export let titulo
    export let descripcion
    export let imagen

    function ver() {
        dispatch('ver-mas',{id: 'Archivo Json'}); // En detail está el id
    }

    function favorito() {
        dispatch('favorito', 'Saludos'); // En detail solo está 'Saludos'
    }
</script>

<div class="card" style="width: 18res;">
    <img src={imagen} alt={titulo} width="100%" height="100%">
    <div class="card-body">
        <h5 class="card-title">{titulo}</h5>
        <p class="card-text">{descripcion}</p>
        <button on:click={ver} class="btn btn-primary"> Ver más...</button>
        <button on:click={favorito} class="btn btn-danger"> Favorito</button>
    </div>
</div>
