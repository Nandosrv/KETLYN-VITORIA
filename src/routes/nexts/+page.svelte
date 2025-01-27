<script>
    import { goto } from "$app/navigation";
    import { fade, fly } from 'svelte/transition';
    import homeone from "$lib/images/homeone.png";

    function nextPage() {
        goto("/nexts/nextp");
    }

    function goBack() {
        window.history.back();
    }
</script>

<div class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <img src={homeone || "/placeholder.svg"} alt="Imagem de fundo romântica" class="absolute w-full h-full object-cover" />
    
    <div class="absolute inset-0  bg-opacity-60"></div>

    <div class="relative z-10 p-8 rounded-lg shadow-2xl max-w-lg w-full md:max-w-2xl text-center text-white backdrop-blur-sm bg-white bg-opacity-10" in:fade={{ duration: 1000 }}>
        <div in:fly={{ y: 50, duration: 1000, delay: 300 }}>
            <h2 class="text-3xl font-bold mb-6 text-red-300">Nossa História</h2>
            
            <p class="text-lg sm:text-xl mb-6 leading-relaxed text-black">
                Março de 2023, o dia que vive em minha memória e 2 anos em que amadureci e não consigo parar de pensar em te fazer feliz de verdade.
            </p>
            <p class="text-lg sm:text-xl mb-6 leading-relaxed text-black">
                Aprendi que o amor é livre e ao mesmo tempo, na base de respeito e confiança.
            </p>
            <p class="text-lg sm:text-xl mb-6 leading-relaxed text-black">
                Esse tempo longe de você, só me fez ter a certeza de que eu te amo e quero fazer tudo para ter o seu perdão e te fazer feliz de verdade.
            </p>

            <div class="flex flex-col sm:flex-row justify-between mt-8 space-y-4 sm:space-y-0 sm:space-x-4">
                <button
                    class="bg-gray-600 text-white px-6 py-3 rounded-full hover:bg-gray-700 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-gray-400 focus:ring-opacity-50"
                    on:click={goBack}
                >
                    Voltar
                </button>

                <button
                    class="bg-red-500 text-white px-6 py-3 rounded-full hover:bg-red-600 transition-all duration-300 text-lg font-semibold transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-red-400 focus:ring-opacity-50"
                    on:click={nextPage}
                >
                    Próxima página
                </button>
            </div>
        </div>
    </div>
</div>

<style>
    :global(body) {
        background-color: #000;
    }
</style>