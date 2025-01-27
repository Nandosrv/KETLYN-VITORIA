<script>
    import { goto } from "$app/navigation";
    import { fade, fly } from 'svelte/transition';
    import { onMount } from 'svelte';
    import home5 from "$lib/images/home5.png";
    import Love from "../../../../../../componentes/love.svelte";

    function nextPage() {
        goto("/nexts/nextp/nexto/nextq");
    }

    function goBack() {
        window.history.back();
    }

    let visible = false;

    onMount(() => {
        setTimeout(() => {
            visible = true;
        }, 100); // Atraso de 100ms para garantir que a transição seja visível
    });
</script>

<div class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <!-- Imagem de fundo -->
    <img src={home5 || "/placeholder.svg"} alt="Imagem de fundo romântica" class="absolute w-full h-full object-cover" />
    
    <div class="absolute inset-0 bg-opacity-60"></div>

    <!-- Main content com animação -->
    <main class="relative z-10 w-full max-w-4xl px-4 py-8">
        {#if visible}
            <!-- Transições de Fade e Fly aplicadas -->
            <div in:fade={{ duration: 1000 }}>
                <div 
                    class="bg-white bg-opacity-90 p-8 rounded-lg shadow-2xl max-w-2xl mx-auto text-center"
                    in:fly={{ y: 50, duration: 1000 }}
                >
                    <p class="text-lg sm:text-xl mb-8 leading-relaxed text-gray-800 italic">
                        Eu não quero voltar ao passado,<br>
                        quero construir um presente que você queira ficar.<br>
                        Porque amor não é só memória,<br>
                        é escolha — e eu escolho te amar.
                    </p>
                    <div class=" w-full h-[100px] flex justify-center items-center">
                        <Love />
                    </div>
                    <div class="flex flex-col sm:flex-row justify-center items-center space-y-4 sm:space-y-0 sm:space-x-4">
                        <button
                            class="bg-gray-600 text-white px-6 py-3 rounded-full hover:bg-gray-700 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-gray-400 focus:ring-opacity-50 w-full sm:w-auto"
                            on:click={goBack}
                        >
                            Voltar
                        </button>

                        <!-- Descomente para adicionar o botão "Próxima página" -->
                        <!-- <button
                            class="bg-red-500 text-white px-6 py-3 rounded-full hover:bg-red-600 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-red-400 focus:ring-opacity-50 w-full sm:w-auto"
                            on:click={nextPage}
                        >
                            Próxima página
                        </button> -->
                    </div>
                </div>
            </div>
        {/if}
    </main>
</div>

<style>
    :global(body) {
        background-color: #000;
    }

    /* Para garantir que a imagem de fundo cubra toda a tela */
    img {
        object-fit: cover;
    }
</style>
