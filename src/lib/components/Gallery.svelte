<script lang="ts">
  const images = [
    'https://images.unsplash.com/photo-1613977257363-31169399859b?q=80&w=2000&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1598928506311-c55ded91a20c?q=80&w=2000&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1582268611958-ebfd161ef9cf?q=80&w=2000&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1600585154340-be6161a56a0c?q=80&w=2000&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1570129477492-45c003edd2be?q=80&w=2000&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1605276374104-dee2a0ed3cd6?q=80&w=2000&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1512917774080-9991f1c4c750?q=80&w=2000&auto=format&fit=crop',
    'https://images.unsplash.com/photo-1572120360610-d971b9d7767c?q=80&w=2000&auto=format&fit=crop',
  ];
</script>

<section id="gallery" class="py-20 bg-gray-50">
  <div class="container mx-auto px-6">
    <p class="text-sm uppercase text-gray-500">[ GALLERY ]</p>
    <h2 class="text-4xl font-bold text-gray-800 my-4">Explore the Villa</h2>

    <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
      {#each images as image, i}
        <div class:col-span-2={i === 0 || i === 5} class:row-span-2={i === 0 || i === 5}>
          <img
            src={image}
            alt="Villa Gallery Image {i + 1}"
            class="h-full w-full object-cover rounded-lg shadow-md"
          />
        </div>
      {/each}
    </div>
  </div>
</section>
