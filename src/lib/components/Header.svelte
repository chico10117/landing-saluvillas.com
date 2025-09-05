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

<header class="fixed top-0 left-0 right-0 z-50 bg-white bg-opacity-90 backdrop-blur-md shadow-md">
  <div class="container mx-auto px-6 py-4 flex justify-between items-center">
    <div class="flex items-center space-x-3 text-2xl font-bold text-gray-800">
      <!-- Salu Villas Logo -->
      <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg" class="text-gray-800">
        <!-- Villa roof -->
        <path d="M4 18L16 6L28 18V28H20V20H12V28H4V18Z" fill="currentColor" opacity="0.8"/>
        <!-- Villa base -->
        <rect x="6" y="20" width="4" height="8" fill="currentColor" opacity="0.6"/>
        <rect x="22" y="20" width="4" height="8" fill="currentColor" opacity="0.6"/>
        <!-- Windows -->
        <rect x="13" y="16" width="2" height="2" fill="white"/>
        <rect x="17" y="16" width="2" height="2" fill="white"/>
        <!-- Door -->
        <rect x="14.5" y="22" width="3" height="6" fill="white" rx="1"/>
        <!-- Pool -->
        <ellipse cx="16" cy="30" rx="8" ry="1.5" fill="#3B82F6" opacity="0.7"/>
        <!-- Palm tree accent -->
        <circle cx="26" cy="14" r="1" fill="#10B981"/>
        <path d="M25 14C25 13 25.5 12 26 12C26.5 12 27 13 27 14" stroke="#10B981" stroke-width="0.5" fill="none"/>
      </svg>
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
      class="cta-button hidden md:inline-block bg-gray-800 text-white px-6 py-2 rounded-md hover:bg-gray-700 transition-colors duration-200 font-semibold"
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
    <div class="md:hidden bg-white border-t border-gray-200 shadow-lg relative z-50">
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
          class="cta-button block w-full text-left bg-gray-800 text-white px-4 py-2 rounded-md hover:bg-gray-700 transition-colors duration-200 mt-4 font-semibold"
        >
          Book a Stay
        </button>
      </nav>
    </div>
  {/if}
</header>

<style>
  button {
    border: none;
    cursor: pointer;
    font-family: inherit;
    font-size: inherit;
  }
  
  /* Nav buttons should have no background */
  nav button {
    background: none;
  }
  
  /* CTA button should keep its background */
  .cta-button {
    background: rgb(31 41 55) !important; /* gray-800 */
  }
  
  .cta-button:hover {
    background: rgb(55 65 81) !important; /* gray-700 */
  }
</style>
