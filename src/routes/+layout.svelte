<script lang="ts">
	import Header from './Header.svelte';
	import '../app.css';
    import Footer from '../componentes/footer.svelte';

	let { children } = $props();
</script>

<div class="app">
	<!-- <Header /> -->
	<header class="fixed top-0 left-0 w-full p-4 bg-white text-pink-600 flex justify-between items-center shadow-lg">
		<a href="/" class="text-xl font-semibold">
		  <span class="text-3xl">❤️</span> 
		  Voltar à Página Principal
		</a>
	  </header>
	<main>
		{@render children()}
	</main>

	
</div>

<!-- <style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style> -->
