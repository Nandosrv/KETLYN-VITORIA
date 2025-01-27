<script lang="ts">
  import { goto } from '$app/navigation';
  import pnj1 from '$lib/images/pnj1.png';
  import pnj2 from '$lib/images/pnj2.png';
  import pnj3 from '$lib/images/pnj3.png';
  import pnj4 from '$lib/images/pnj4.png';
  import foto1 from '$lib/images/1.jpg';
  import foto2 from '$lib/images/2.jpg';
  import foto3 from '$lib/images/3.jpg';
  import foto4 from '$lib/images/4.jpg';
  import foto5 from '$lib/images/5.jpg';
  import foto6 from '$lib/images/6.jpg';
  import foto7 from '$lib/images/7.jpg';
  import foto8 from '$lib/images/8.jpg';
  import foto9 from '$lib/images/9.jpg';
  import foto10 from '$lib/images/10.jpg';
  import foto11 from '$lib/images/11.jpg';
  import foto12 from '$lib/images/12.jpg';
  import foto13 from '$lib/images/13.jpg';
  import foto14 from '$lib/images/14.jpg';
  import foto15 from '$lib/images/15.jpg';
  import foto16 from '$lib/images/16.jpg';
  import foto17 from '$lib/images/17.jpg';
  import foto18 from '$lib/images/18.jpg';
  import foto19 from '$lib/images/19.jpg';
  import foto20 from '$lib/images/20.mp4';
  import foto21 from '$lib/images/21.mp4';

  import Footer from '../../componentes/footer.svelte';

  const imagens = [pnj1, pnj2, pnj3, pnj4, foto1, foto2, foto3, foto4, foto5, foto6, foto7, foto8, foto9, foto10, foto11, foto12, foto13, foto14, foto15, foto16, foto17, foto18, foto19];
  const videos = [foto20, foto21];

  const declaracoes = [
    "Cada clique me lembra do quanto você é especial para mim.",
    "Esta foto é uma das muitas memórias que guardo com tanto carinho.",
    "O brilho no seu olhar nesta foto é o que mais me faz sorrir.",
    "Nunca deixarei de lembrar desse momento maravilhoso que vivemos.",
    "Você é a razão das minhas melhores lembranças, e esta foto prova isso.",
    "Quando olho para essa foto, sinto que cada segundo ao seu lado valeu a pena.",
    "Nosso amor é eterno, e cada foto como essa é um lembrete disso.",
    "Esta foto captura a essência do que é estar ao seu lado.",
    "As melhores lembranças que tenho de você estão todas aqui, e eu nunca as apagarei.",
    "Eu me apaixono por você novamente cada vez que olho para essa foto.",
    "Cada imagem é um pedaço do meu coração guardado para sempre.",
    "O que mais me encanta é ver como você sempre ilumina qualquer ambiente.",
    "Cada foto é um pedaço de um amor que nunca vai acabar.",
    "Com você, cada instante se torna inesquecível, e essas fotos são testemunhas disso.",
    "A cada imagem que olho fico feliz, e isso é para sempre.",
    "Eu guardo todas essas fotos porque elas são meu jeito de manter você perto de mim.",
    "Cada foto é um lembrete de como sou abençoado por ter feito parte da sua vida.",
    "Não importa quantas fotos, nenhuma delas vai apagar o que sinto por você.",
    "Essas imagens são a prova de que o amor nunca desaparece, e o nosso é eterno.",
    "Essas imagens são a prova de que o amor nunca desaparece, e o nosso é eterno.",
    "Essas imagens são a prova de que o amor nunca desaparece, e o nosso é eterno.",
    "Cada foto me faz lembrar de como cada momento contigo é único."
  ];

  let showModal = false;
  let currentImage = '';
  let currentVideo = '';

  const openModal = (content: string) => {
    if (content.endsWith('.mp4')) {
      currentVideo = content;
      currentImage = '';
    } else {
      currentImage = content;
      currentVideo = '';
    }
    showModal = true;
  };

  const closeModal = () => {
    showModal = false;
    currentImage = '';
    currentVideo = '';
  };

  const disableRightClick = (event: MouseEvent) => {
    event.preventDefault();
  };
</script>

<main class="mt-13 flex items-center justify-center h-screen bg-gradient-to-r from-purple-500 to-pink-500 text-white">
  <div class="text-center p-8 rounded-lg bg-white bg-opacity-20 shadow-lg w-full max-w-5xl">
      <h1 class="text-3xl font-semibold mb-4">Nosso Álbum</h1>
      <p class="mb-8">Aqui estão alguns dos momentos especiais que compartilhamos juntos.</p>
      
      <!-- Grid de imagens -->
      <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-6">
          {#each imagens as imagem, index}
              <!-- svelte-ignore a11y_click_events_have_key_events -->
              <div 
                role="button" 
                tabindex="0" 
                on:click={() => openModal(imagem)} 
                class="rounded-lg overflow-hidden shadow-lg hover:scale-105 transition-transform cursor-pointer">
                  <img src={imagem} alt={`Imagem ${index + 1}`} class="w-full h-48 object-cover"/>
                  <div class="p-4 bg-gray-800 text-white">
                      <p class="text-center mt-2 text-sm italic">{declaracoes[index]}</p>
                  </div>
              </div>
          {/each}

          <!-- Grid de vídeos -->
          {#each videos as video, index}
              <!-- svelte-ignore a11y_click_events_have_key_events -->
              <div 
                role="button" 
                tabindex="0" 
                on:click={() => openModal(video)} 
                class="rounded-lg overflow-hidden shadow-lg hover:scale-105 transition-transform cursor-pointer">
                  <video 
                    class="w-full h-48 object-cover" 
                    src={video} 
                    controls
                    on:contextmenu={disableRightClick}>
                    <track kind="captions" srcLang="en" label="English"/>
                    Seu navegador não suporta vídeo.
                  </video>
                  <div class="p-4 bg-gray-800 text-white">
                      <p class="text-center">Eu Te Amo</p>
                  </div>
              </div>
          {/each}
      </div>

      {#if showModal}
        <div class="fixed inset-0 bg-black bg-opacity-75 flex items-center justify-center z-50">
          <div class="relative bg-white p-8 rounded-lg max-w-3xl w-full">
            <button 
              class="absolute top-0 right-0 bg-gray-800 text-white px-4 py-2 rounded-full hover:bg-gray-700"
              on:click={closeModal}>
              Fechar
            </button>
            {#if currentImage}
              <img src={currentImage} alt="Imagem" class="max-w-full max-h-screen"/>
            {/if}
            {#if currentVideo}
              <!-- svelte-ignore a11y_media_has_caption -->
              <video class="max-w-full max-h-screen" src={currentVideo} controls autoplay>
                Seu navegador não suporta vídeo.
              </video>
            {/if}
          </div>
        </div>
      {/if}

      <button 
          class="mt-8 bg-pink-600 px-6 py-2 text-white rounded-lg hover:bg-pink-700 transition-all"
          on:click={() => goto('/')} >
          Voltar
      </button>
  </div>
  
</main>

<Footer />
