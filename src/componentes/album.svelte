<script>
    import { goto } from '$app/navigation';
  </script>
  
  <main class="flex items-center justify-center h-screen bg-gradient-to-r from-purple-500 to-pink-500 text-white">
    <div class="text-center p-8 rounded-lg bg-white bg-opacity-20 shadow-lg w-96">
      <h1 class="text-3xl font-semibold mb-4">Nosso Álbum</h1>
      <p class="mb-8">Aqui estão alguns dos momentos especiais que compartilhamos juntos.</p>
      <!-- Adicione imagens aqui -->
      <div class="grid grid-cols-2 gap-4">
        <img src="https://via.placeholder.com/150" alt="Imagem 1" class="rounded-lg shadow-lg" />
        <img src="https://via.placeholder.com/150" alt="Imagem 2" class="rounded-lg shadow-lg" />
        <img src="https://via.placeholder.com/150" alt="Imagem 3" class="rounded-lg shadow-lg" />
        <img src="https://via.placeholder.com/150" alt="Imagem 4" class="rounded-lg shadow-lg" />
      </div>
      <button 
        class="mt-8 bg-pink-600 px-6 py-2 text-white rounded-lg hover:bg-pink-700 transition-all"
        on:click={() => goto('/')}
      >
        Voltar
      </button>
    </div>
  </main>
  