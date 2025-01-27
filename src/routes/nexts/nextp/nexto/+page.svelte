<script>
    import { goto } from "$app/navigation";
    import { fade, fly } from 'svelte/transition';
    import { onMount } from 'svelte';
    import home3 from "$lib/images/home3.png";

    function nextPage() {
        goto("/nexts/nextp/nexto/nextq");
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
    <img src={home3 || "/placeholder.svg"} alt="Imagem de fundo romântica" class="absolute w-full h-full object-cover" />
    
    <div class="absolute inset-0  bg-opacity-40"></div>

    <main class="relative z-10 w-full max-w-4xl px-4 py-8">
        {#if visible}
            <div in:fade={{ duration: 1000 }}>
                <div 
                    class="bg-white bg-opacity-90 p-8 rounded-lg shadow-2xl max-w-2xl mx-auto text-center text-black"
                    in:fly={{ y: 50, duration: 1000 }}
                >
                    <p class="text-lg sm:text-xl mb-6 leading-relaxed italic">
                        Se hoje fosse o dia em que te visse pela primeira vez,
                        ainda perderia o fôlego ao cruzar teu olhar.
                        Entre tantas, só você seria capaz
                        de transformar o comum em poesia, o instante em eternidade.
                    </p>

                    <div class="flex flex-col sm:flex-row justify-center items-center space-y-4 sm:space-y-0 sm:space-x-4 mt-8">
                        <button
                            class="bg-gray-600 text-white px-6 py-3 rounded-full hover:bg-gray-700 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-gray-400 focus:ring-opacity-50 w-full sm:w-auto"
                            on:click={goBack}
                        >
                            Voltar
                        </button>

                        <button
                            class="bg-red-500 text-white px-6 py-3 rounded-full hover:bg-red-600 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-red-400 focus:ring-opacity-50 w-full sm:w-auto"
                            on:click={nextPage}
                        >
                            Próxima página
                        </button>
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
</style>

