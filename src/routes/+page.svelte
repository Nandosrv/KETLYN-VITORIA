<script>
	import { onMount } from 'svelte';
	import home from '$lib/images/home.png';
	import { goto } from '$app/navigation';
  
	let visible = false;

	onMount(() => {
		setTimeout(() => {
			visible = true;
		}, 2000); // Tempo do "loading" (em milissegundos)
	});

	function openLetter() {
		goto('/nexts');
	}
</script>

<div class="relative min-h-screen overflow-hidden">
  <!-- Background image with overlay -->
  <img src={home} alt="Imagem de fundo" class="absolute w-full h-full object-cover z-0" />
  <div class="absolute inset-0 bg-opacity-40 z-10"></div>

  <!-- Content -->
  <div class="relative z-20 min-h-screen flex items-center justify-center px-4 sm:px-6 lg:px-8">
    <div class="w-full max-w-lg">
      <!-- Loading - Heart Animation -->
      <div class={`absolute ${visible ? 'opacity-0' : 'opacity-100'} transition-all duration-1000`}>
        <div class="flex justify-center items-center space-x-2">
          <div class="w-12 h-12 border-4 border-t-transparent border-red-500 rounded-full animate-spin"></div> <!-- Spinner -->
          <div class="text-red-500 text-4xl animate-pulse">💖</div> <!-- Heart Animation -->
        </div>
      </div>

      <!-- Main Content -->
      <div class={`text-center transform transition-all duration-1000 ease-out ${visible ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'}`}>
        <!-- Título -->
        <h1 class="text-[#F44210] text-4xl sm:text-5xl md:text-6xl font-bold mb-6 shadow-text">
          KETLYN VITÓRIA
        </h1>

        <!-- Pergunta -->
        <p class="text-xl sm:text-2xl md:text-3xl text-black mb-8 shadow-text">
          Se nos conhecêssemos hoje, será que você me daria a chance de te fazer feliz como você merece?
        </p>

        <!-- Subtítulo -->
        <h2 class="text-2xl sm:text-3xl md:text-4xl font-bold text-red-400 mb-6 shadow-text">
          Para o amor da minha vida
        </h2>

        <!-- Texto de ação -->
        <p class="text-lg sm:text-xl text-black mb-8 shadow-text">
          Clique para abrir esta carta de amor...
        </p>

        <!-- Botão de clique -->
        <button
          class="px-8 py-4 bg-red-500 text-white font-bold text-lg rounded-full hover:bg-pink-600 transition-all duration-300 transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-pink-400 focus:ring-opacity-50"
          on:click={openLetter}
        >
          Abrir Carta
        </button>
      </div>
    </div>
  </div>
</div>

<style>
  .shadow-text {
    text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
  }
</style>
