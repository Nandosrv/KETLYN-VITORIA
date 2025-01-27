<script lang="ts">
  import { goto } from '$app/navigation';
  import Footer from '../componentes/footer.svelte';
</script>

<svelte:head>
  <title>Uma Carta de Amor</title>
  <meta name="description" content="Uma página especial para expressar amor" />
</svelte:head>

<main class="relative flex flex-col items-center justify-center min-h-screen bg-gradient-to-br from-pink-500 via-red-500 to-orange-500 text-white px-4 py-8 overflow-hidden">
  
  <!-- Fundo com corações flutuantes -->
  <div class="absolute top-0 left-0 w-full h-full bg-gradient-to-br from-pink-600 to-yellow-500 opacity-50"></div>

  <!-- Corações voando -->
  <div class="absolute top-0 left-0 w-full h-full pointer-events-none">
    {#each Array(10) as _, i}
      <div class="heart absolute animate-heart" style="animation-delay: {i * 1}s; left: {Math.random() * 100}%; bottom: -100px;">
        ❤️
      </div>
    {/each}
  </div>

  <div 
    class="text-center p-8 rounded-2xl bg-white bg-opacity-20 backdrop-blur-md shadow-xl max-w-md w-full mx-auto transform transition-all duration-300 hover:scale-105"
  >
    <h1 class="text-4xl md:text-5xl font-bold mb-6 text-red-600">Uma Carta de Amor</h1>
    <p class="mb-8 text-lg md:text-xl text-black leading-relaxed">"Você é o motivo do meu sorriso, meu amor eterno..."</p>
    
    <div class="space-y-4">
      {#each [{text: 'Ver Álbum', route: '/album'}, {text: 'Iniciar Quiz', route: '/quiz'}] as button}
        <button 
          class="w-full bg-red-500 px-6 py-3 text-white rounded-lg transition-all duration-300 transform hover:bg-pink-700 hover:scale-105 focus:outline-none focus:ring-2 focus:ring-pink-400 focus:ring-opacity-50"
          on:click={() => goto(button.route)}
          aria-label={button.text}
        >
          {button.text}
        </button>
      {/each}
    </div>
  </div>

  <Footer />

</main>

<style lang="postcss">
  /* Estilo de fundo 3D com gradiente */
  main {
    perspective: 1500px;
  }

  .heart {
    font-size: 2rem;
    opacity: 0;
    animation: float 6s ease-in-out infinite;
  }

  /* Animação dos corações flutuando */
  @keyframes float {
    0% {
      transform: translateY(0) rotate(0deg);
      opacity: 1;
    }
    50% {
      transform: translateY(-200px) rotate(180deg);
      opacity: 0.5;
    }
    100% {
      transform: translateY(-400px) rotate(360deg);
      opacity: 0;
    }
  }

  /* Efeito de transformação de fundo */
  .absolute {
    position: absolute;
  }

  .animate-heart {
    animation: float 6s ease-in-out infinite;
  }

  /* Adicionando o efeito de perspectiva ao fundo */
  .bg-gradient-to-br {
    background: linear-gradient(to bottom right, rgba(255, 105, 180, 0.7), rgba(255, 140, 0, 0.7));
  }

</style>
