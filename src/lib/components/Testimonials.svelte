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
  ];

  let currentTestimonial = 0;

  function next() {
    currentTestimonial = (currentTestimonial + 1) % testimonials.length;
  }

  function prev() {
    currentTestimonial = (currentTestimonial - 1 + testimonials.length) % testimonials.length;
  }
</script>

<section id="testimonials" class="py-20">
  <div class="container mx-auto px-6">
    <p class="text-sm uppercase text-gray-500">[ THE GUESTBOOK ]</p>
    <h2 class="text-4xl font-bold text-gray-800 my-4">What our guests are saying about us</h2>

    <div class="relative">
      <div class="overflow-hidden">
        <div
          class="flex transition-transform duration-500 ease-in-out"
          style="transform: translateX(-{currentTestimonial * 100}%)"
        >
          {#each testimonials as testimonial}
            <div class="w-full flex-shrink-0">
              <div class="bg-white p-8 rounded-lg shadow-lg max-w-2xl mx-auto">
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
                <p class="text-gray-600 text-lg italic">"{testimonial.quote}"</p>
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
        class="absolute top-1/2 left-0 md:-left-16 transform -translate-y-1/2 bg-white p-2 rounded-full shadow-md hover:bg-gray-100"
      >
        &larr;
      </button>
      <button
        on:click={next}
        class="absolute top-1/2 right-0 md:-right-16 transform -translate-y-1/2 bg-white p-2 rounded-full shadow-md hover:bg-gray-100"
      >
        &rarr;
      </button>
    </div>
  </div>
</section>
