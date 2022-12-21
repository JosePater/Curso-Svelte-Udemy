<script>
    // Variables a exportar
    export let control;
    export let value;
    export let placeholder;
    export let type;
    export let nombre;
    export let id;
</script>

<div class="form-group">
    <p {id}>{nombre}</p>
    <!-- <label {id}>{nombre}</label> -->
    {#if control ==='textarea'}
        <textarea {id} {placeholder} {value} on:input class="form-control" rows="10"></textarea>
    {:else}
        <input {id} {type} {placeholder} {value} on:input class="form-control">
    {/if}
</div>