<script>
    import Card from "./Card.svelte";
    export let post;
    let evento = 'Sin eventos'; 

    function verMas(e) {
        alert("Has llamado a la función verMas");
        evento = e.detail.id; // Guarda el id de detail
    }

    function favorito(event) {
        alert("Has llamado a la función favorito");
        evento = event.detail; // guarda lo que hay en datail

    }

</script>

<div class="row mt-3">
    {#each post as item}
        <div class="col-sm-3">
            <Card
                titulo={item.titulo}
                descripcion={item.descripcion}
                imagen={item.imagen}
                on:ver-mas={verMas}
                on:favorito={favorito} />
        </div>
    {/each}
</div>
<h1>{evento}</h1>