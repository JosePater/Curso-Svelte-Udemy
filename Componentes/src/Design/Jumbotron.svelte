<script>
    export let nombre;
</script>

<div class="jumbotron mt-4">
    <h1>{nombre}</h1>
    <!-- Permite agregar más elementos cuando se llama al componente de la forma tradicional -->
    <slot></slot>
</div>