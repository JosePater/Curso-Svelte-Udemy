<script>
    export let nombre;
    let mostrar;
    // Función llamada con el mouse
    function entrar() {
        mostrar = true;
    }
    // Función llamada con el mouse
    function salir() {
        mostrar = false;
    }
</script>

<div class="jumbotron mt-4" on:mouseenter={entrar} on:mouseleave={salir}>
    <h1>{nombre}</h1>
    <h2>
        <!-- Permite agregar más elementos cuando se llama al componente de la forma tradicional -->
        <slot name="subtitulo">
            <span>Agregar subtítulos aquí</span>
        </slot>
    </h2>
    <p>
        <slot name="parrafo">
            <span>Aquí va un párrafo</span>
        </slot>
    </p>
    <slot mostrar={mostrar}></slot>
</div>

<style>
    h2 {
        color: red;
        font-weight: bolder;
        text-decoration:overline;
    }
    p{
        text-align: justify;
        color: blue;
        text-transform: uppercase;
        font-style: italic;
    }
</style>
