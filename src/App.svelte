<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
 
  
  // Alan Walker discography
  const discography = [
    {
      title: "Faded",
      year: 2015,
      image: "../../static/images/faded.jpg",
      description: "One of Alan Walker's biggest hits that reached #1 in multiple countries."
    },
    {
      title: "Alone",
      year: 2016,
      image: "../../static/images/alone.jpg",
      description: "Follow-up single that solidified Walker's signature sound."
    },
    {
      title: "Sing Me to Sleep",
      year: 2016,
      image: "../../static/images/sing-me-to-sleep.jpg",
      description: "Released after the huge success of 'Faded'."
    },
    {
      title: "All Falls Down",
      year: 2017,
      image: "../../static/images/all-falls-down.jpg",
      description: "Collaboration with Noah Cyrus and Digital Farm Animals."
    },
    {
      title: "Darkside",
      year: 2018,
      image: "../../static/images/darkside.jpg",
      description: "Part of the 'World of Walker' trilogy."
    },
  ];
  
  // Timeline events
  const timeline = [
    { year: 1997, event: "Born on August 24 in Northampton, England" },
    { year: 2012, event: "Started producing music under the name DJ Walkzz" },
    { year: 2014, event: "Released 'Fade' on NoCopyrightSounds" },
    { year: 2015, event: "Released 'Faded', a remastered vocal version of 'Fade'" },
    { year: 2016, event: "Released 'Alone' and 'Sing Me to Sleep'" },
    { year: 2018, event: "Released his debut album 'Different World'" },
    { year: 2021, event: "Released the album 'World of Walker'" }
  ];
  
  let showMusicPlayer = false;
  let darkMode = false;
  
  function toggleDarkMode() {
    darkMode = !darkMode;
    document.documentElement.classList.toggle('dark');
  }
  
  onMount(() => {
    showMusicPlayer = true;
  });
</script>

<svelte:head>
  <title>Alan Walker Tribute | Electronic Music Pioneer</title>
  <meta name="description" content="A tribute to Alan Walker, the electronic music producer behind hits like Faded and Alone.">
</svelte:head>

<div class={darkMode ? "dark" : ""}>
  <div class="bg-gray-100 dark:bg-gray-900 text-gray-800 dark:text-gray-200 min-h-screen transition-colors duration-300">
    <!-- Hero Section -->
    <header class="relative h-screen flex items-center justify-center overflow-hidden">
      <div class="absolute top-0 left-0 w-full h-full bg-black opacity-50 z-10"></div>
      <div 
        class="absolute top-0 left-0 w-full h-full bg-cover bg-center z-0" 
        style="background-image: url('/images/alan-walker-bg.jpg');"
      ></div>
      
      <div class="container mx-auto px-4 z-20 text-center">
        <div in:fade={{ duration: 1000, delay: 300 }}>
          <h1 class="text-5xl md:text-7xl font-bold text-white mb-4">Alan Walker</h1>
          <p class="text-xl md:text-2xl text-gray-200 mb-8">Electronic Music Producer & DJ</p>
          <div class="flex justify-center gap-4">
            <button 
              class="bg-blue-600 hover:bg-blue-700 text-white py-2 px-6 rounded-full transition-all duration-300 transform hover:scale-105"
              on:click={() => document.getElementById('about').scrollIntoView({ behavior: 'smooth' })}
            >
              Learn More
            </button>
            <!-- <button 
              class="bg-transparent border-2 border-white text-white py-2 px-6 rounded-full hover:bg-white hover:text-black transition-all duration-300"
              on:click={toggleDarkMode}
            >
              {darkMode ? 'Light Mode' : 'Dark Mode'}
            </button> -->
          </div>
        </div>
      </div>
      
      <div class="absolute bottom-10 left-0 right-0 flex justify-center animate-bounce">
        <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
        </svg>
      </div>
    </header>
    
    <!-- About Section -->
    <section id="about" class="py-20 bg-white dark:bg-gray-800">
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row items-center">
          <div class="md:w-1/2 mb-10 md:mb-0">
            <div class="relative">
              <div class="absolute -inset-1 bg-gradient-to-r from-blue-600 to-purple-600 rounded-lg blur opacity-25"></div>
              <div class="relative bg-white dark:bg-gray-800 p-2 rounded-lg">
                <img 
                  src="../../static/images/alan-walker-profile.jpg" 
                  alt="Alan Walker" 
                  class="rounded-lg w-full shadow-lg"
                />
              </div>
            </div>
          </div>
          <div class="md:w-1/2 md:pl-12">
            <h2 class="text-3xl font-bold mb-6">About Alan Walker</h2>
            <p class="text-lg mb-6">
              Alan Olav Walker was born on August 24, 1997, in Northampton, England. He is a British-Norwegian DJ and record producer, best known for his internationally acclaimed single "Faded" (2015), which received platinum certifications in over 10 countries.
            </p>
            <p class="text-lg mb-6">
              Walker started his career as a self-taught producer releasing tracks on YouTube and SoundCloud. His breakthrough came when he released "Fade" in 2014, which later became "Faded" with added vocals. The signature sound of his productions combines elements of electronic dance music with emotional melodies.
            </p>
            <p class="text-lg">
              Walker is also known for his distinctive image, often appearing with a face mask and hoodie, creating a mysterious persona that has become part of his brand identity.
            </p>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Discography Section -->
    <section class="py-20 bg-gray-100 dark:bg-gray-900">
      <div class="container mx-auto px-4">
        <h2 class="text-4xl font-bold text-center mb-16">Discography</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {#each discography as album, i}
            <div 
              class="bg-white dark:bg-gray-800 rounded-lg overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2"
              in:fly={{ y: 50, duration: 600, delay: i * 200 }}
            >
              <div class="h-48 bg-gray-200 dark:bg-gray-700 overflow-hidden">
                <img 
                  src={album.image} 
                  alt={album.title} 
                  class="w-full h-full object-cover transition-transform duration-500 hover:scale-110"
                />
              </div>
              <div class="p-6">
                <div class="flex justify-between items-center mb-2">
                  <h3 class="text-xl font-bold">{album.title}</h3>
                  <span class="text-sm text-gray-500 dark:text-gray-400">{album.year}</span>
                </div>
                <p class="text-gray-600 dark:text-gray-300">{album.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
    </section>
    
    <!-- Timeline Section -->
    <section class="py-20 bg-white dark:bg-gray-800">
      <div class="container mx-auto px-4">
        <h2 class="text-4xl font-bold text-center mb-16">Career Timeline</h2>
        <div class="relative">
          <!-- Timeline Line -->
          <div class="absolute left-1/2 transform -translate-x-1/2 h-full w-1 bg-blue-600"></div>
          
          <!-- Timeline Events -->
          {#each timeline as item, i}
            <div class="relative mb-12">
              <div class={`flex items-center ${i % 2 === 0 ? 'flex-row-reverse' : ''}`}>
                <div class="w-1/2"></div>
                <div class="absolute left-1/2 transform -translate-x-1/2 w-4 h-4 rounded-full bg-blue-600 border-4 border-white dark:border-gray-800 z-10"></div>
                <div class={`w-1/2 ${i % 2 === 0 ? 'pr-12 text-right' : 'pl-12'}`}>
                  <div 
                    class="bg-gray-100 dark:bg-gray-700 p-6 rounded-lg shadow-md hover:shadow-lg transition-all duration-300"
                    in:fly={{ x: i % 2 === 0 ? -50 : 50, duration: 600, delay: i * 150 }}
                  >
                    <h3 class="text-xl font-bold mb-2">{item.year}</h3>
                    <p class="text-gray-600 dark:text-gray-300">{item.event}</p>
                  </div>
                </div>
              </div>
            </div>
          {/each}
        </div>
      </div>
    </section>
    
    <!-- Music Player -->
    <!-- {#if showMusicPlayer}
      <div 
        class="fixed bottom-0 left-0 right-0 bg-gray-900 text-white py-4 shadow-lg z-50 transition-all duration-500"
        in:fly={{ y: 50, duration: 800 }}
      >
        <div class="container mx-auto px-4">
          <div class="flex items-center justify-between">
            <div class="flex items-center">
              <div class="w-12 h-12 rounded-md overflow-hidden mr-4">
                <img src="/images/faded.jpg" alt="Now Playing" class="w-full h-full object-cover" />
              </div>
              <div>
                <h4 class="font-bold">Faded</h4>
                <p class="text-sm text-gray-400">Alan Walker</p>
              </div>
            </div>
            
            <div class="flex-1 mx-8 hidden md:block">
              <div class="flex items-center">
                <span class="text-xs mr-2">0:00</span>
                <div class="flex-1 h-1 bg-gray-700 rounded-full">
                  <div class="w-1/3 h-full bg-blue-600 rounded-full"></div>
                </div>
                <span class="text-xs ml-2">3:32</span>
              </div>
            </div>
            
            <div class="flex items-center space-x-4">
              <button class="text-gray-400 hover:text-white transition-colors">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12.066 11.2a1 1 0 000 1.6l5.334 4A1 1 0 0019 16V8a1 1 0 00-1.6-.8l-5.333 4zM4.066 11.2a1 1 0 000 1.6l5.334 4A1 1 0 0011 16V8a1 1 0 00-1.6-.8l-5.334 4z"></path>
                </svg>
              </button>
              <button class="bg-blue-600 w-10 h-10 rounded-full flex items-center justify-center hover:bg-blue-700 transition-colors">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"></path>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                </svg>
              </button>
              <button class="text-gray-400 hover:text-white transition-colors">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11.933 12.8a1 1 0 000-1.6L6.6 7.2A1 1 0 005 8v8a1 1 0 001.6.8l5.333-4zM19.933 12.8a1 1 0 000-1.6l-5.333-4A1 1 0 0013 8v8a1 1 0 001.6.8l5.333-4z"></path>
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    {/if}
     -->
    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-12">
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="mb-6 md:mb-0">
            <h2 class="text-2xl font-bold mb-2">Alan Walker</h2>
            <p class="text-gray-400">Electronic Music Producer & DJ</p>
          </div>
          
          <div class="flex space-x-6">
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors">
              <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
              </svg>
            </a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors">
              <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
              </svg>
            </a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors">
              <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                <path d="M19.615 3.184c-3.604-.246-11.631-.245-15.23 0-3.897.266-4.356 2.62-4.385 8.816.029 6.185.484 8.549 4.385 8.816 3.6.245 11.626.246 15.23 0 3.897-.266 4.356-2.62 4.385-8.816-.029-6.185-.484-8.549-4.385-8.816zm-10.615 12.816v-8l8 3.993-8 4.007z"/>
              </svg>
            </a>
            <a href="#" class="text-gray-400 hover:text-blue-600 transition-colors">
              <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                <path d="M9 8h-3v4h3v12h5v-12h3.642l.358-4h-4v-1.667c0-.955.192-1.333 1.115-1.333h2.885v-5h-3.808c-3.596 0-5.192 1.583-5.192 4.615v3.385z"/>
              </svg>
            </a>
          </div>
        </div>
        
        <hr class="border-gray-800 my-8" />
        
        <div class="text-center text-gray-500 text-sm">
          <p>© 2025 Alan Walker Tribute Page | Created with SvelteKit & Tailwind CSS</p>
          <p class="mt-2">This is a fan-made tribute page and is not affiliated with Alan Walker or his management.</p>
        </div>
      </div>
    </footer>
  </div>
</div>
