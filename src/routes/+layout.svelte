<script>
	import '../app.css';
	let { children } = $props();
</script>

<header class="bg-orange-600 p-6 text-white shadow-lg">
	<div class="container mx-auto flex flex-col items-center justify-between md:flex-row">
		<h1 class="text-3xl font-bold tracking-tight transition duration-300 hover:text-orange-200">
			crudSencillo
		</h1>
		<nav class="mt-4 md:mt-0">
			<ul class="flex space-x-6">
				<li>
					<a
						href="/bienvenida"
						class="text-lg font-semibold transition duration-300 hover:text-orange-200 hover:underline"
						>Inicio</a
					>
				</li>
				<li>
					<a
						href="/productos"
						class="text-lg font-semibold transition duration-300 hover:text-orange-200 hover:underline"
						>Productos</a
					>
				</li>
			</ul>
		</nav>
	</div>
</header>

{@render children()}
