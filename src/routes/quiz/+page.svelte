<script>
    import { fly } from 'svelte/transition';
    import { goto } from '$app/navigation';
    import frit from '$lib/images/pnj1.png'
    import gigi from '$lib/images/gigi.gif'
    let answers = {
      q1: '',
      q2: '',
      q3: '',
      q4: '',
      q5: ''
    };
    
    let currentPage = 1;  // Controla qual pergunta está sendo exibida
    let showResult = false;
    let finalMessage = '';
    let apologyMessage = '';
    let apologyTriggered = false;
    
    // Caminho da imagem (substitua pelo caminho correto da imagem dela)
    const imageUrl = '/path/to/your/image.jpg';
  
    /**
     * @param {string} question
     * @param {string} answer
     */
    function submitAnswer(question, answer) {
      // @ts-ignore
      answers[question] = answer;
      currentPage += 1;
    
      if (answers.q1 === 'nao' || answers.q2 === 'nao' || answers.q3 === 'nao' || answers.q4 === 'nao' || answers.q5 === 'nao') {
        apologyTriggered = true;
        apologyMessage = "Sei que errei em muitos momentos e te magoei, e por isso, peço desculpas do fundo do meu coração. O tempo sem você me fez perceber o quanto você é importante pra mim, e eu só queria uma chance de corrigir as falhas do passado. Estou aqui, de coração aberto, pronto para recomeçar e fazer tudo dar certo. Você merece o melhor, e eu quero ser a pessoa que vai te dar isso. Por favor, me dê uma chance!";
      }
    
      if (currentPage === 6) {
        let score = Object.values(answers).filter(answer => answer === 'sim').length;
    
        if (score === 5) {
          finalMessage = "Eu sei que o tempo passou e que a distância entre nós aumentou, mas, no fundo, nunca te esqueci. Cada dia sem você foi uma lembrança do quanto você significa pra mim. Eu ainda sinto a mesma saudade, o mesmo amor, e quero lutar para reconquistar o que perdemos. Me dê uma chance de fazer tudo certo, de reconstruir o que nós dois sabemos que ainda pode ser lindo. Eu te amo e vou te amar para sempre.";
        } else if (score >= 3) {
          finalMessage = "Os dois anos sem você me fizeram refletir sobre tudo o que vivemos e o que ainda poderia ser. Eu sei que a vida mudou, mas meu amor por você nunca se apagou. Não quero mais perder tempo. Quero que possamos tentar novamente, com mais maturidade, mais compreensão. Eu sei que podemos superar o que nos afastou, e quero reconstruir algo ainda mais forte e verdadeiro entre nós.";
        } else {
          finalMessage = "Eu sei que o tempo é implacável, mas o que sinto por você nunca desapareceu. Talvez o que vivemos tenha sido marcado por erros, mas estou pronto para corrigir e recomeçar. Se você me der a chance, quero lutar pelo nosso amor e pela felicidade que sempre imaginei ao seu lado. Estou aqui, com o coração aberto, esperando um novo começo.";
        }
        showResult = true;
      }
    }
  </script>
  
  <main class="flex items-center justify-center h-screen bg-gradient-to-r from-yellow-500 to-red-500 text-white">
    <div class="text-center p-8 rounded-lg bg-red-500 bg-opacity-20 shadow-lg w-96">
      <h1 class="text-3xl font-semibold mb-4">Quiz do Amor: 2 Anos de Distância</h1>
      <p class="mb-4">Dois anos se passaram, e sei que muitas coisas mudaram, mas o que não mudou foi o meu amor por você. Vamos refletir juntos?</p>
      
      <!-- Exibindo a imagem dela -->
      <img src={gigi} alt="Imagem da pessoa amada" class="w-32 h-32 rounded-full mx-auto mb-4 object-cover" />
      <!-- <video class="w-32 h-32 rounded-full mx-auto mb-4 object-cover" src={gigi} controls>
    </video>
     -->
      {#if !showResult}
        {#if currentPage === 1}
          <div class="p-4 mb-4 rounded-lg bg-white bg-opacity-20 shadow-md" in:fly={{ y: 30, duration: 300 }}>
            <p class="text-lg font-medium text-black">1. Mesmo com tanto tempo sem nos vermos, você ainda sente algo por mim?</p>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-4" on:click={() => submitAnswer('q1', 'sim')}>Sim</button>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-2" on:click={() => submitAnswer('q1', 'nao')}>Não</button>
          </div>
        {/if}
  
        {#if currentPage === 2}
          <div class="p-4 mb-4 rounded-lg bg-white bg-opacity-20 shadow-md" in:fly={{ y: 30, duration: 300 }}>
            <p class="text-lg font-medium text-black">2. Você acha que o amor que sentimos um pelo outro pode superar o tempo que passamos separados?</p>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-4" on:click={() => submitAnswer('q2', 'sim')}>Sim</button>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-2" on:click={() => submitAnswer('q2', 'nao')}>Não</button>
          </div>
        {/if}
  
        {#if currentPage === 3}
          <div class="p-4 mb-4 rounded-lg bg-white bg-opacity-20 shadow-md" in:fly={{ y: 30, duration: 300 }}>
            <p class="text-lg font-medium text-black">3. Você sente falta dos momentos que passamos juntos?</p>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-4" on:click={() => submitAnswer('q3', 'sim')}>Sim</button>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-2" on:click={() => submitAnswer('q3', 'nao')}>Não</button>
          </div>
        {/if}
  
        {#if currentPage === 4}
          <div class="p-4 mb-4 rounded-lg bg-white bg-opacity-20 shadow-md" in:fly={{ y: 30, duration: 300 }}>
            <p class="text-lg font-medium text-black">4. Você acredita que podemos superar os erros do passado e recomeçar do zero?</p>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-4" on:click={() => submitAnswer('q4', 'sim')}>Sim</button>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-2" on:click={() => submitAnswer('q4', 'nao')}>Não</button>
          </div>
        {/if}
  
        {#if currentPage === 5}
          <div class="p-4 mb-4 rounded-lg bg-white bg-opacity-20 shadow-md" in:fly={{ y: 30, duration: 300 }}>
            <p class="text-lg font-medium text-black">5. Se eu pedisse para tentarmos de novo, você estaria disposto(a) a tentar?</p>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-4" on:click={() => submitAnswer('q5', 'sim')}>Sim</button>
            <button class="bg-pink-600 px-6 py-2 text-white rounded-lg mt-2" on:click={() => submitAnswer('q5', 'nao')}>Não</button>
          </div>
        {/if}
      {:else}
        <div class="mb-8">
          <p class="text-xl font-semibold mb-4">Resultado:</p>
          {#if apologyTriggered}
            <p class="italic">{apologyMessage}</p>
          {:else}
            <p class="italic">{finalMessage}</p>
          {/if}
        </div>
  
        <button 
          class="mt-4 bg-pink-600 px-6 py-2 text-white rounded-lg hover:bg-pink-700 transition-all"
          on:click={() => goto('/')}
        >
          Voltar para a Página Principal
        </button>
      {/if}
    </div>
  </main>
  