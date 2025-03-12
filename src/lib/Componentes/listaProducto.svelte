<script>
	export let productos;
	export let onEditarProductos;
	export let onEliminarProductos;
</script>

<div>
	{#if productos.length === 0}
		<div class="mb-2 font-bold">No hay productos agregados</div>
	{:else}
		<div class="px-4 font-bold">
			<span class="mr-25">Nombre</span>
			<span class="mr-25">Tipo</span>
			<span>Precio</span>
		</div>
	{/if}

	<ul class="mt-4 space-y-4">
		{#each productos as producto, index}
			<li
				class="flex items-center justify-between rounded-lg border-b bg-gray-50 px-4 py-4 shadow-sm transition duration-200 hover:bg-gray-100"
			>
				<span class="text-lg font-medium">{producto.nombre}</span>
				<span class="text-sm text-gray-600">{producto.tipo}</span>
				<span class="text-lg font-bold">${producto.precio}</span>
				<div>
					<button
						on:click={() => onEditarProductos(index)}
						class="mr-2 w-24 rounded-md bg-blue-500 p-1 text-white">Editar</button
					>
					<button
						on:click={() => onEliminarProductos(index)}
						class="w-24 rounded-md bg-red-500 p-1 text-white">Eliminar</button
					>
				</div>
			</li>
		{/each}
	</ul>
</div>
