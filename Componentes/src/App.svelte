<script>
	// Importar componentes
	import Header from "./Design/Header.svelte";
	import CardGrid from "./Posts/CardGrid.svelte";
	import InputCustom from "./Design/InputCustom.svelte";
	import Jumbotron from "./Design/Jumbotron.svelte";
	const color = "warning";
	
	// Variables para el nuevo Post
	let titulo = "";
	let descripcion = "";
	let imagen = "";

	let post = [
		{
			id: "1",
			titulo: "Trabajando con svelte",
			descripcion: "Realizando el curso de svelte a medio día",
			imagen: "https://cdn.pixabay.com/photo/2021/12/09/22/17/table-setting-6859276_960_720.jpg",
		},
		{
			id: "2",
			titulo: "Trabajando con Vue",
			descripcion: "Realizando el curso de svelte por la tarde",
			imagen: "https://cdn.pixabay.com/photo/2015/01/08/18/27/startup-593341_960_720.jpg",
		},
		{
			id: "3",
			titulo: "Trabajando con Angular",
			descripcion: "Realizando el curso de svelte por la noche",
			imagen: "https://cdn.pixabay.com/photo/2022/12/03/13/01/butterfly-7632646_960_720.jpg",
		},
	];

	// Función para agregar un nuevo Post
	function agregarPost() {
		if (imagen == "") {
			imagen = "https://media.istockphoto.com/id/1204299297/photo/blank-flat-square-gift-box-with-hinged-flap-lid.jpg?b=1&s=170667a&w=0&k=20&c=rJXLoAwK6nftvzELSrQ0uKp6vuyIujezKx1Jy7x_GDY=";
		} 
		const nuevoPost = {
			id: Math.random().toString(),
			titulo: titulo,
			descripcion: descripcion,
			imagen: imagen
		};

		// Los '...post' mantiene los datos anteriores del Array
		// Para agregar nuevos post al final se colocar la función al final
		post = [...post,nuevoPost];
	}
</script>

<!-- Se llama el componente importado -->
<Header titulo="Primer componente" {color} />
<Header titulo="Segundo componente" color="info" />

<div class="container">
	<!-- Contenedor para llamar el componente Card -->

	<!-- Se llama el componente de la manera tradicional (con su etiqueta de cierre) -->
	<Jumbotron nombre="Mis componentes" let:mostrar={mostrar}>
		<span slot="subtitulo">
			<!-- Reemplaza lo que está dentro del span en el jumbotron.svelte -->
			Curso de Svelte 
		</span>
		<span slot="parrafo">
			Contenido del párrafo
		</span>
		<hr>
		<div class:mostrar>
			{#if mostrar == true}
			<button class="btn btn-danger">Botón</button>
			{:else}
			<h2>Coloca el mouse encima</h2>
			{/if}
		</div>
	</Jumbotron>

	<CardGrid {post} />
	<!-- Llama el componente CardGrid -->
	<hr />

	<!-- preventDefault: evita que se refresque la página -->
	<form on:submit|preventDefault={agregarPost}> 
		<!-- Al dar clic llama  -->
		
		<InputCustom
			type='text'
			nombre='Titulo'
			id='titulo'
			placeholder='Título'
			value={titulo}
			on:input = {event => (titulo = event.target.value)}
		/>
		<InputCustom
			type='text'
			nombre='Imagen'
			id='imgen'
			placeholder='Imagen'
			value={imagen}
			on:input = {event => (imagen = event.target.value)}
		/>
		<InputCustom
			control='textarea'
			nombre='Descripción'
			id='descripicion'
			placeholder='Descripción'
			value={descripcion}
			on:input = {event => (descripcion = event.target.value)}
		/>
		<button type="submit" class="btn btn-info">Guardar</button>
	</form>
</div>
