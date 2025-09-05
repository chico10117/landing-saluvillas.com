<!-- A full-screen hero section with a background image and centered text. -->
<section
  class="relative h-screen bg-cover bg-center"
  style="background-image: url('https://images.unsplash.com/photo-1580587771525-78b9dba3b914?q=80&w=3000&auto=format&fit=crop');"
>
  <div class="absolute inset-0 bg-black opacity-40"></div>
  <div class="relative z-10 flex flex-col items-center justify-center h-full text-white text-center">
    <h1 class="text-5xl md:text-7xl font-bold leading-tight mb-4">
      DIFFERENT STAYS IN BEAUTIFUL COSTA RICA
    </h1>
    <p class="text-lg md:text-xl mb-8">
      Your private luxury villa in Guanacaste. Welcome to your new home.
    </p>
    <button 
      on:click={() => {
        const element = document.getElementById('gallery');
        if (element) {
          const headerHeight = 80;
          const elementPosition = element.offsetTop - headerHeight;
          window.scrollTo({
            top: elementPosition,
            behavior: 'smooth'
          });
        }
      }}
      class="bg-white text-gray-800 px-8 py-3 rounded-md font-semibold hover:bg-gray-200 transition-colors duration-200"
    >
      Explore the Villa
    </button>
  </div>
</section>
