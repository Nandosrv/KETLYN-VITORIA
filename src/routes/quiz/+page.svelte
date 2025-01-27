<script>
    import { goto } from '$app/navigation';
  
    let answers = {
      q1: '',
      q2: '',
      q3: '',
      q4: '',
      q5: ''
    };
  
    let showResult = false;
    let finalMessage = '';
    let apologyMessage = '';
    let apologyTriggered = false; // Inicializando a variável corretamente
  
    // Função para calcular a resposta final com base nas respostas do quiz
    function submitQuiz() {
      let score = 0;
  
      // Verificando as respostas
      if (answers.q1 === 'sim') score++;
      if (answers.q2 === 'sim') score++;
      if (answers.q3 === 'sim') score++;
      if (answers.q4 === 'sim') score++;
      if (answers.q5 === 'sim') score++;
  
      // Se houver algum "não", ajusta a mensagem para pedido de desculpas
      if (answers.q1 === 'nao' || answers.q2 === 'nao' || answers.q3 === 'nao' || answers.q4 === 'nao' || answers.q5 === 'nao') {
        apologyTriggered = true; // Ajustando o estado para "true" caso alguma resposta seja "não"
        apologyMessage = "Sei que errei em muitos momentos e te magoei, e por isso, peço desculpas do fundo do meu coração. O tempo sem você me fez perceber o quanto você é importante pra mim, e eu só queria uma chance de corrigir as falhas do passado. Estou aqui, de coração aberto, pronto para recomeçar e fazer tudo dar certo. Você merece o melhor, e eu quero ser a pessoa que vai te dar isso. Por favor, me dê uma chance!";
      }
  
      // Definindo a mensagem final com base nas respostas
      if (score === 5) {
        finalMessage = "Eu sei que o tempo passou e que a distância entre nós aumentou, mas, no fundo, nunca te esqueci. Cada dia sem você foi uma lembrança do quanto você significa pra mim. Eu ainda sinto a mesma saudade, o mesmo amor, e quero lutar para reconquistar o que perdemos. Me dê uma chance de fazer tudo certo, de reconstruir o que nós dois sabemos que ainda pode ser lindo. Eu te amo e vou te amar para sempre.";
      } else if (score >= 3) {
        finalMessage = "Os dois anos sem você me fizeram refletir sobre tudo o que vivemos e o que ainda poderia ser. Eu sei que a vida mudou, mas meu amor por você nunca se apagou. Não quero mais perder tempo. Quero que possamos tentar novamente, com mais maturidade, mais compreensão. Eu sei que podemos superar o que nos afastou, e quero reconstruir algo ainda mais forte e verdadeiro entre nós.";
      } else {
        finalMessage = "Eu sei que o tempo é implacável, mas o que sinto por você nunca desapareceu. Talvez o que vivemos tenha sido marcado por erros, mas estou pronto para corrigir e recomeçar. Se você me der a chance, quero lutar pelo nosso amor e pela felicidade que sempre imaginei ao seu lado. Estou aqui, com o coração aberto, esperando um novo começo.";
      }
  
      showResult = true;
    }
  </script>
  
  <main class="flex items-center justify-center h-screen bg-gradient-to-r from-yellow-500 to-red-500 text-white">
    <div class="text-center p-8 rounded-lg bg-black bg-opacity-20 shadow-lg w-96">
      <h1 class="text-3xl font-semibold mb-4">Quiz do Amor: 2 Anos de Distância</h1>
      <p class="mb-4">Dois anos se passaram, e sei que muitas coisas mudaram, mas o que não mudou foi o meu amor por você. Vamos refletir juntos?</p>
  
      {#if !showResult}
        <!-- Perguntas do Quiz -->
        <div class="mb-4">
          <p class="text-lg font-medium">1. Mesmo com tanto tempo sem nos vermos, você ainda sente algo por mim?</p>
          <input type="radio" id="q1-sim" bind:group={answers.q1} value="sim" />
          <label for="q1-sim" class="ml-2">Sim</label>
          <input type="radio" id="q1-nao" bind:group={answers.q1} value="nao" />
          <label for="q1-nao" class="ml-2">Não</label>
        </div>
  
        <div class="mb-4">
          <p class="text-lg font-medium">2. Você acha que o amor que sentimos um pelo outro pode superar o tempo que passamos separados?</p>
          <input type="radio" id="q2-sim" bind:group={answers.q2} value="sim" />
          <label for="q2-sim" class="ml-2">Sim</label>
          <input type="radio" id="q2-nao" bind:group={answers.q2} value="nao" />
          <label for="q2-nao" class="ml-2">Não</label>
        </div>
  
        <div class="mb-4">
          <p class="text-lg font-medium">3. Você sente falta dos momentos que passamos juntos?</p>
          <input type="radio" id="q3-sim" bind:group={answers.q3} value="sim" />
          <label for="q3-sim" class="ml-2">Sim</label>
          <input type="radio" id="q3-nao" bind:group={answers.q3} value="nao" />
          <label for="q3-nao" class="ml-2">Não</label>
        </div>
  
        <div class="mb-4">
          <p class="text-lg font-medium">4. Você acredita que podemos superar os erros do passado e recomeçar do zero?</p>
          <input type="radio" id="q4-sim" bind:group={answers.q4} value="sim" />
          <label for="q4-sim" class="ml-2">Sim</label>
          <input type="radio" id="q4-nao" bind:group={answers.q4} value="nao" />
          <label for="q4-nao" class="ml-2">Não</label>
        </div>
  
        <div class="mb-4">
          <p class="text-lg font-medium">5. Se eu pedisse para tentarmos de novo, você estaria disposto(a) a tentar?</p>
          <input type="radio" id="q5-sim" bind:group={answers.q5} value="sim" />
          <label for="q5-sim" class="ml-2">Sim</label>
          <input type="radio" id="q5-nao" bind:group={answers.q5} value="nao" />
          <label for="q5-nao" class="ml-2">Não</label>
        </div>
  
        <button 
          class="bg-pink-600 px-6 py-2 text-white rounded-lg hover:bg-pink-700 transition-all"
          on:click={submitQuiz}
        >
          Submeter Respostas
        </button>
      {:else}
        <!-- Resultado e Desabafo -->
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
  