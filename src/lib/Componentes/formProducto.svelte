<!-- src/lib/Componentes/formProducto.svelte -->
<script>
	export let NuevosProductos;
	export let editando;
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	function handleEnviar() {
		dispatch('agregarProductos'); // Emitir el evento al padre
	}
</script>

<form on:submit|preventDefault={handleEnviar} class="mb-4 flex flex-col md:flex-row md:space-x-2">
	<input
		type="text"
		bind:value={NuevosProductos.nombre}
		class="mb-2 flex-1 border p-2 md:mb-0"
		placeholder="Nombre del producto"
	/>
	<input
		type="text"
		bind:value={NuevosProductos.tipo}
		class="mb-2 flex-1 border p-2 md:mb-0"
		placeholder="Tipo del producto"
	/>
	<input
		type="number"
		bind:value={NuevosProductos.precio}
		class="mb-2 flex-1 border p-2 md:mb-0"
		placeholder="Precio del producto"
	/>
	<button type="submit" class="rounded-md bg-blue-500 p-2 text-white">
		{editando !== null ? 'Actualizar' : 'Agregar'}
	</button>
</form>
