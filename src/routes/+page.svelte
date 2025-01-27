<script>
  import { goto } from '$app/navigation';
</script>

<main class="flex items-center justify-center h-screen bg-gradient-to-r from-pink-500 to-red-500 text-white">
  <div class="text-center p-8 rounded-lg bg-white bg-opacity-20 shadow-lg w-96">
    <h1 class="text-3xl font-semibold mb-4">Uma Carta de Amor</h1>
    <p class="mb-8">"Você é o motivo do meu sorriso, meu amor eterno..."</p>
    <button 
      class="bg-pink-600 px-6 py-2 text-white rounded-lg mb-4 hover:bg-pink-700 transition-all"
      on:click={() => goto('/album')}
    >
      Ver Álbum
    </button>
    <button 
      class="bg-pink-600 px-6 py-2 text-white rounded-lg hover:bg-pink-700 transition-all"
      on:click={() => goto('/quiz')}
    >
      Iniciar Quiz
    </button>
  </div>
</main>
