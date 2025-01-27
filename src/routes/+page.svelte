<script lang="ts">
  import { fly, fade } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';
  import { goto } from '$app/navigation';
  import Footer from '../componentes/footer.svelte';

  let hoveredButton: string | null = null;
</script>

<svelte:head>
  <title>Uma Carta de Amor</title>
  <meta name="description" content="Uma página especial para expressar amor" />
</svelte:head>

<main class="flex flex-col items-center justify-center min-h-screen bg-gradient-to-br from-pink-500 via-red-500 to-orange-500 text-white px-4 py-8">
  <div 
    class="text-center p-8 rounded-2xl bg-white bg-opacity-20 backdrop-blur-md shadow-xl max-w-md w-full mx-auto transform transition-all duration-300 hover:scale-105"
    in:fly="{{ y: 50, duration: 1000, easing: quintOut }}"
  >
    <h1 class="text-4xl md:text-5xl font-bold mb-6 text-red-600">Uma Carta de Amor</h1>
    <p class="mb-8 text-lg md:text-xl text-black leading-relaxed">"Você é o motivo do meu sorriso, meu amor eterno..."</p>
    
    <div class="space-y-4">
      {#each [{text: 'Ver Álbum', route: '/album'}, {text: 'Iniciar Quiz', route: '/quiz'}] as button}
        <button 
          class="w-full bg-red-500 px-6 py-3 text-white rounded-lg transition-all duration-300 transform hover:bg-pink-700 hover:scale-105 focus:outline-none focus:ring-2 focus:ring-pink-400 focus:ring-opacity-50"
          on:click={() => goto(button.route)}
          on:mouseenter={() => hoveredButton = button.text}
          on:mouseleave={() => hoveredButton = null}
          aria-label={button.text}
        >
          {button.text}
          {#if hoveredButton === button.text}
            <span in:fade="{{ duration: 200 }}" class="ml-2">❤️</span>
          {/if}
        </button>
      {/each}
    </div>
  </div>
</main>

<Footer />

<style lang="postcss">
 
</style>