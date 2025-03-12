<script>
	import FormProducto from '$lib/Componentes/formProducto.svelte';
	import ListaProducto from '$lib/Componentes/listaProducto.svelte';

	let productos = [];
	let NuevosProductos = {
		nombre: '',
		tipo: '',
		precio: ''
	};
	let editando = null;

	function agregarProductos() {
		const precioString = String(NuevosProductos.precio).trim();

		if (NuevosProductos.nombre.trim() && NuevosProductos.tipo.trim() && precioString) {
			if (editando !== null) {
				productos[editando] = { ...NuevosProductos, precio: precioString };
				editando = null;
			} else {
				productos = [...productos, { ...NuevosProductos, precio: precioString }];
			}
			NuevosProductos = { nombre: '', tipo: '', precio: '' };
		} else {
			console.log('Por favor, completa todos los campos.');
		}
	}

	function eliminarProductos(index) {
		console.log('Eliminando producto en el índice:', index);
		productos = productos.filter((_, i) => i !== index);
	}

	function editarProductos(index) {
		console.log('Editando producto en el índice:', index);
		NuevosProductos = { ...productos[index] };
		editando = index;
	}
</script>

<main class="flex flex-col items-center p-4">
	<div class="w-full max-w-3xl rounded-lg bg-white p-6 shadow-md">
		<h2 class="mb-4 text-center text-xl font-bold">
			{editando !== null ? 'Editar Producto' : 'Agregar Producto'}
		</h2>
		<FormProducto {NuevosProductos} {editando} on:agregarProductos={agregarProductos} />

		<ListaProducto
			{productos}
			onEditarProductos={editarProductos}
			onEliminarProductos={eliminarProductos}
		/>
	</div>
</main>
