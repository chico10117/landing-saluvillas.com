<script lang="ts">
  let mobileMenuOpen = false;

  function scrollToSection(sectionId: string) {
    const element = document.getElementById(sectionId);
    if (element) {
      const headerHeight = 80; // Approximate header height
      const elementPosition = element.offsetTop - headerHeight;
      
      window.scrollTo({
        top: elementPosition,
        behavior: 'smooth'
      });
      
      mobileMenuOpen = false; // Close mobile menu after navigation
    }
  }

  function toggleMobileMenu() {
    mobileMenuOpen = !mobileMenuOpen;
  }
</script>

<header class="fixed top-0 left-0 right-0 z-10 bg-white bg-opacity-90 backdrop-blur-md shadow-md">
  <div class="container mx-auto px-6 py-4 flex justify-between items-center">
    <div class="text-2xl font-bold text-gray-800">
      <a href="/" on:click={() => window.scrollTo({ top: 0, behavior: 'smooth' })}>SALU VILLAS</a>
    </div>
    <nav class="hidden md:flex items-center space-x-8">
      <button 
        on:click={() => scrollToSection('about')} 
        class="text-gray-600 hover:text-gray-800 transition-colors duration-200"
      >
        About
      </button>
      <button 
        on:click={() => scrollToSection('features')} 
        class="text-gray-600 hover:text-gray-800 transition-colors duration-200"
      >
        The Villa
      </button>
      <button 
        on:click={() => scrollToSection('gallery')} 
        class="text-gray-600 hover:text-gray-800 transition-colors duration-200"
      >
        Gallery
      </button>
      <button 
        on:click={() => scrollToSection('contact')} 
        class="text-gray-600 hover:text-gray-800 transition-colors duration-200"
      >
        Contact
      </button>
    </nav>
    <button 
      on:click={() => scrollToSection('contact')} 
      class="hidden md:inline-block bg-gray-800 text-white px-6 py-2 rounded-md hover:bg-gray-700 transition-colors duration-200"
    >
      Book a Stay
    </button>
    
    <!-- Mobile menu button -->
    <button 
      on:click={toggleMobileMenu}
      class="md:hidden p-2 rounded-md hover:bg-gray-100 transition-colors duration-200"
      aria-label="Toggle mobile menu"
    >
      <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        {#if mobileMenuOpen}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        {:else}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        {/if}
      </svg>
    </button>
  </div>
  
  <!-- Mobile menu -->
  {#if mobileMenuOpen}
    <div class="md:hidden bg-white border-t border-gray-200 shadow-lg">
      <nav class="px-6 py-4 space-y-4">
        <button 
          on:click={() => scrollToSection('about')} 
          class="block w-full text-left text-gray-600 hover:text-gray-800 py-2 transition-colors duration-200"
        >
          About
        </button>
        <button 
          on:click={() => scrollToSection('features')} 
          class="block w-full text-left text-gray-600 hover:text-gray-800 py-2 transition-colors duration-200"
        >
          The Villa
        </button>
        <button 
          on:click={() => scrollToSection('gallery')} 
          class="block w-full text-left text-gray-600 hover:text-gray-800 py-2 transition-colors duration-200"
        >
          Gallery
        </button>
        <button 
          on:click={() => scrollToSection('contact')} 
          class="block w-full text-left text-gray-600 hover:text-gray-800 py-2 transition-colors duration-200"
        >
          Contact
        </button>
        <button 
          on:click={() => scrollToSection('contact')} 
          class="block w-full text-left bg-gray-800 text-white px-4 py-2 rounded-md hover:bg-gray-700 transition-colors duration-200 mt-4"
        >
          Book a Stay
        </button>
      </nav>
    </div>
  {/if}
</header>

<style>
  button {
    background: none;
    border: none;
    cursor: pointer;
    font-family: inherit;
    font-size: inherit;
  }
</style>
