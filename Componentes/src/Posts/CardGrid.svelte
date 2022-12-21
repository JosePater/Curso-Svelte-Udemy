<script>
    import Card from "./Card.svelte";
    export let post;

    function verMas() {
        alert("Has llamado a la función verMas");
    }

    function favorito() {
        alert("Has llamado a la función favorito");
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
