<script setup>
import { ref } from 'vue';

const filmovi = [
  { 
    naslov: "Gospodar prstenova: Prstenova družina", 
    slika: "https://m.media-amazon.com/images/I/71lKy8RoFUL._AC_UF1000,1000_QL80_.jpg"
  },
  { 
    naslov: "Gospodar prstenova: Dvije kule", 
    slika: "https://m.media-amazon.com/images/M/MV5BMGQxMDdiOWUtYjc1Ni00YzM1LWE2NjMtZTg3Y2JkMjEzMTJjXkEyXkFqcGc@._V1_FMjpg_UX1000_.jpg"
  },
  { 
    naslov: "Gospodar prstenova: Povratak kralja", 
    slika: "https://m.media-amazon.com/images/M/MV5BMTZkMjBjNWMtZGI5OC00MGU0LTk4ZTItODg2NWM3NTVmNWQ4XkEyXkFqcGc@._V1_.jpg"
  }
];

const isDarkMode = ref(true);

const promjeniPozadinu = () => {
  isDarkMode.value = !isDarkMode.value;
};
</script>

<template>
  <div class="min-h-screen flex items-center justify-center p-4 transition-colors duration-300"
    :class="{'bg-gray-900 text-white': isDarkMode, 'bg-white text-gray-900': !isDarkMode}">

    <button @click="promjeniPozadinu" class="fixed top-4 right-4 bg-gray-800 text-white p-2 rounded-full shadow-lg">
      Prebaci na svijetli/tamni način
    </button>

    <div class="p-6 md:p-8 rounded-2xl w-full max-w-[1024px] shadow-2xl transition-all duration-500"
      :class="{'bg-gradient-to-br from-emerald-950 to-indigo-950': isDarkMode, 'bg-gradient-to-br from-emerald-300 to-indigo-300': !isDarkMode}">

      <h1 class="text-3xl md:text-4xl font-bold text-center">Pozdrav, ja sam Marija Kurić</h1>

      <h2 class="text-md md:text-lg text-center mt-4">Moji omiljeni filmovi:</h2>

      <div class="flex flex-wrap justify-center gap-4 md:gap-6 mt-6">
        <div v-for="film in filmovi" :key="film.naslov"
             class="w-[160px] h-[230px] sm:w-[200px] sm:h-[280px] md:w-[280px] md:h-[400px] 
                    overflow-hidden rounded-lg shadow-lg transition-transform duration-300 hover:scale-105">
          <img :src="film.slika" :alt="film.naslov" class="w-full h-full object-cover">
        </div>
      </div>

      <div class="flex flex-wrap justify-center gap-3 md:gap-4 mt-4 text-sm md:text-lg">
        <span v-for="film in filmovi" :key="film.naslov">{{ film.naslov }}</span>
      </div>

    </div>
  </div>
</template>

