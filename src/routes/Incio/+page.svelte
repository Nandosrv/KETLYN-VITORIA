<script>
    let cartaAberta = false;
  </script>
  
  <div class="min-h-screen flex justify-center items-center bg-gradient-to-r from-pink-200 to-purple-200">
    <!-- svelte-ignore a11y_click_events_have_key_events -->
    <!-- svelte-ignore a11y_no_static_element_interactions -->
    <div class="relative w-96 h-96 cursor-pointer" on:click={() => cartaAberta = true}>
      <!-- Carta fechada -->
      {#if !cartaAberta}
        <div class="w-full h-full bg-white rounded-lg shadow-lg transform transition-all duration-300 hover:scale-105 flex justify-center items-center text-2xl text-gray-700 font-semibold p-8">
          <p>Abra minha carta</p>
        </div>
      {/if}
      
      <!-- Carta aberta -->
      {#if cartaAberta}
        <div class="w-full h-full bg-white rounded-lg shadow-lg p-8 transform transition-all duration-300 opacity-100">
          <h1 class="text-3xl font-bold text-pink-600 mb-6 animate-fade-in">Minha Declaração de Amor</h1>
          <p class="text-lg text-gray-800 animate-fade-in">
            Lembro de cada momento ao seu lado, cada sorriso, cada palavra... Você tem o poder de fazer meu coração bater mais forte a cada dia. Eu não consigo imaginar minha vida sem você. Te amo mais a cada segundo.
          </p>
        </div>
      {/if}
    </div>
  </div>
  
  <style>
    @keyframes fade-in {
      0% { opacity: 0; }
      100% { opacity: 1; }
    }
  
    .animate-fade-in {
      animation: fade-in 1s ease-out;
    }
  </style>
  