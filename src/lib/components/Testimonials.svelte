<script lang="ts">
  const testimonials = [
    {
      quote:
        'Our stay was an unforgettable experience. The apartment was beautifully restored, perfectly clean, and the attention to detail was pure magic!',
      author: 'Sofia & Mateus',
      rating: 5,
    },
    {
      quote:
        'From the moment we arrived, we were blown away by the beauty of the villa and the warmth of the staff. A true paradise.',
      author: 'John & Jane Doe',
      rating: 5,
    },
    {
      quote:
        'The perfect escape. We enjoyed the stunning sunsets from the infinity pool every evening. We will be back!',
      author: 'The Smiths',
      rating: 5,
    },
    {
      quote:
        'Absolutely stunning property with breathtaking ocean views. The villa exceeded all our expectations and the service was impeccable.',
      author: 'Maria & Carlos',
      rating: 5,
    },
    {
      quote:
        'A hidden gem in Costa Rica! The villa is luxurious, private, and surrounded by incredible natural beauty. Perfect for our honeymoon.',
      author: 'Emma & David',
      rating: 5,
    },
    {
      quote:
        'We felt like we were living in paradise. The infinity pool, the views, and the thoughtful amenities made this trip unforgettable.',
      author: 'The Johnson Family',
      rating: 5,
    },
    {
      quote:
        'The most beautiful villa we have ever stayed in. Every detail was perfect, from the modern design to the incredible location.',
      author: 'Alessandro & Francesca',
      rating: 5,
    },
    {
      quote:
        'An oasis of tranquility and luxury. We loved the spacious rooms, the private pool, and the stunning architecture. Highly recommended!',
      author: 'Michael & Sarah',
      rating: 5,
    },
    {
      quote:
        'This villa is a masterpiece. The blend of modern luxury with natural beauty is extraordinary. We can\'t wait to return!',
      author: 'The Rodriguez Family',
      rating: 5,
    },
    {
      quote:
        'Our group of friends had the most amazing time. The villa was spacious enough for all of us and the location was perfect for exploring Costa Rica.',
      author: 'Lisa & Friends',
      rating: 5,
    },
  ];

  let currentSlide = 0;
  let testimonialsPerView = 1; // Will be updated based on screen size

  // Calculate max slides based on testimonials per view
  $: maxSlides = Math.ceil(testimonials.length / testimonialsPerView) - 1;

  function next() {
    currentSlide = currentSlide >= maxSlides ? 0 : currentSlide + 1;
  }

  function prev() {
    currentSlide = currentSlide <= 0 ? maxSlides : currentSlide - 1;
  }

  // Update testimonials per view based on screen size
  function updateTestimonialsPerView() {
    if (typeof window !== 'undefined') {
      testimonialsPerView = window.innerWidth >= 768 ? 2 : 1;
      // Adjust current slide to prevent going out of bounds
      if (currentSlide > maxSlides) {
        currentSlide = maxSlides;
      }
    }
  }

  // Update on mount and resize
  import { onMount } from 'svelte';
  onMount(() => {
    updateTestimonialsPerView();
    window.addEventListener('resize', updateTestimonialsPerView);
    return () => window.removeEventListener('resize', updateTestimonialsPerView);
  });
</script>

<section id="testimonials" class="py-20">
  <div class="container mx-auto px-6">
    <p class="text-sm uppercase text-gray-500">[ THE GUESTBOOK ]</p>
    <h2 class="text-4xl font-bold text-gray-800 my-4">What our guests are saying about us</h2>

    <div class="relative">
      <div class="overflow-hidden">
        <div
          class="flex transition-transform duration-500 ease-in-out"
          style="transform: translateX(-{currentSlide * (100 / testimonialsPerView)}%)"
        >
          {#each testimonials as testimonial, index}
            <div class="w-full md:w-1/2 flex-shrink-0 px-2">
              <div class="bg-white p-6 md:p-8 rounded-lg shadow-lg h-full flex flex-col">
                <div class="flex items-center mb-4">
                  {#each { length: testimonial.rating } as _, i}
                    <svg
                      class="w-5 h-5 text-yellow-400"
                      fill="currentColor"
                      viewBox="0 0 20 20"
                    >
                      <path
                        d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.286 3.957a1 1 0 00.95.69h4.162c.969 0 1.371 1.24.588 1.81l-3.368 2.448a1 1 0 00-.364 1.118l1.287 3.957c.3.921-.755 1.688-1.539 1.118l-3.368-2.448a1 1 0 00-1.175 0l-3.368 2.448c-.784.57-1.838-.197-1.539-1.118l1.287-3.957a1 1 0 00-.364-1.118L2.05 9.384c-.783-.57-.38-1.81.588-1.81h4.162a1 1 0 00.95-.69L9.049 2.927z"
                      />
                    </svg>
                  {/each}
                </div>
                <p class="text-gray-600 text-lg italic flex-grow">"{testimonial.quote}"</p>
                <p class="text-gray-800 font-semibold mt-4 text-right">
                  - {testimonial.author}
                </p>
              </div>
            </div>
          {/each}
        </div>
      </div>

      <button
        on:click={prev}
        class="absolute top-1/2 left-0 md:-left-16 transform -translate-y-1/2 bg-white p-2 rounded-full shadow-md hover:bg-gray-100 transition-colors duration-200"
        aria-label="Previous testimonials"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
        </svg>
      </button>
      <button
        on:click={next}
        class="absolute top-1/2 right-0 md:-right-16 transform -translate-y-1/2 bg-white p-2 rounded-full shadow-md hover:bg-gray-100 transition-colors duration-200"
        aria-label="Next testimonials"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
        </svg>
      </button>
    </div>

    <!-- Slide indicators -->
    <div class="flex justify-center mt-8 space-x-2">
      {#each { length: maxSlides + 1 } as _, index}
        <button
          on:click={() => currentSlide = index}
          class="w-3 h-3 rounded-full transition-colors duration-200 {currentSlide === index ? 'bg-gray-800' : 'bg-gray-300'}"
          aria-label="Go to slide {index + 1}"
        ></button>
      {/each}
    </div>
  </div>
</section>
