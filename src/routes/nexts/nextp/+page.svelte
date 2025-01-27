<script>
  import { goto } from '$app/navigation';
  import { fade, fly } from 'svelte/transition';
  import { onMount } from 'svelte';
  import hometwo from "$lib/images/hometwo.png";
  import pnj1 from "$lib/images/pnj1.png";
  import pnj2 from "$lib/images/pnj2.png";
  import pnj3 from "$lib/images/pnj3.png";
  import pnj4 from "$lib/images/pnj4.png";

  function nextPage() {
    goto('/nexts/nextp/nexto');
  }

  function goBack() {
    window.history.back();
  }

  let visible = false;

  onMount(() => {
    visible = true;
  });
</script>

<div class="relative min-h-screen flex items-center justify-center overflow-hidden">
  <img src={hometwo || "/placeholder.svg"} alt="Imagem de fundo romântica" class="absolute w-full h-full object-cover" />
  
  <div class="absolute inset-0  bg-opacity-30"></div>

  <main class="relative z-10 w-full max-w-4xl px-4 py-8">
    {#if visible}
      <div in:fade={{ duration: 1000 }}>
        <h1 class="text-3xl md:text-4xl font-bold text-white text-center mb-8 shadow-text" in:fly={{ y: -50, duration: 1000 }}>
          AMO CADA DETALHE SEU!
        </h1>

        <section class="grid grid-cols-2 gap-4 mb-8">
          <div 
            class="bg-white rounded-lg shadow-xl overflow-hidden transform transition-all duration-300 hover:scale-105 hover:shadow-2xl"
            in:fly={{ y: 50, duration: 1000, delay: 300 }}
          >
            <img src={pnj1 || "/placeholder.svg"} alt="Imagem 1" class="w-full h-48 object-cover" />
          </div>
          <div 
            class="bg-white rounded-lg shadow-xl overflow-hidden transform transition-all duration-300 hover:scale-105 hover:shadow-2xl"
            in:fly={{ y: 50, duration: 1000, delay: 450 }}
          >
            <img src={pnj2 || "/placeholder.svg"} alt="Imagem 2" class="w-full h-48 object-cover" />
          </div>
          <div 
            class="bg-white rounded-lg shadow-xl overflow-hidden transform transition-all duration-300 hover:scale-105 hover:shadow-2xl"
            in:fly={{ y: 50, duration: 1000, delay: 600 }}
          >
            <img src={pnj3 || "/placeholder.svg"} alt="Imagem 3" class="w-full h-48 object-cover" />
          </div>
          <div 
            class="bg-white rounded-lg shadow-xl overflow-hidden transform transition-all duration-300 hover:scale-105 hover:shadow-2xl"
            in:fly={{ y: 50, duration: 1000, delay: 750 }}
          >
            <img src={pnj4 || "/placeholder.svg"} alt="Imagem 4" class="w-full h-48 object-cover" />
          </div>
        </section>

        <div class="flex flex-col sm:flex-row justify-between items-center space-y-4 sm:space-y-0">
          <button
            class="bg-gray-600 text-white px-6 py-3 rounded-full hover:bg-gray-700 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-gray-400 focus:ring-opacity-50"
            on:click={goBack}
          >
            Voltar
          </button>

          <button
            class="bg-red-500 text-white px-6 py-3 rounded-full hover:bg-red-600 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-red-400 focus:ring-opacity-50"
            on:click={nextPage}
          >
            Próxima página
          </button>
        </div>
      </div>
    {/if}
  </main>
</div>

<style>
  :global(body) {
    background-color: #000;
  }
  .shadow-text {
    text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
  }
</style>

