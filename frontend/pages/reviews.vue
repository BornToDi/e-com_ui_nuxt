<template>
  <div class="bg-white">
    <div class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8">
      <h2 class="text-lg font-medium text-gray-900">Recent reviews</h2>
      <div class="mt-6 space-y-10 divide-y divide-gray-200 border-b border-t border-gray-200 pb-10">
        <div v-for="review in reviews" :key="review.id" class="pt-10 lg:grid lg:grid-cols-12 lg:gap-x-8">

          <div class="justify-center lg:col-span-4 lg:col-start-1 lg:row-start-1 lg:mt-0 lg:flex-col lg:items-start xl:col-span-3">
            <!-- Display the small and responsive picture -->
            <img
              v-if="review.imageSrc"
              :src="review.imageSrc"
              alt="Reviewer's Image"
              class="h-30 w-40 rounded-full object-cover lg:mb-2 xl:mb-0"
            />

            <div class=" place-items-center mx-5 xl:col-span-1">
              <div class="flex text-center">
                <StarIcon v-for="rating in [0, 1, 2, 3, 4]" :key="rating" :class="[review.rating > rating ? 'text-wild-strawberry-400' : 'text-gray-200', 'h-5 w-5 flex-shrink-0',]" aria-hidden="true" />
                  <p class="ml-3 text-sm text-gray-700  ">{{ review.rating }}<span class="sr-only"> out of 5 stars</span></p>
                </div>
              
            </div>
          </div>

          <div class="lg:col-span-8 lg:col-start-5 xl:col-span-9 xl:col-start-4 xl:grid xl:grid-cols-3 xl:items-start xl:gap-x-8">
   

            <div class="mt-4 lg:mt-6 xl:col-span-2 xl:mt-0">
              <h3 class="text-sm font-medium text-gray-900">{{ review.title }}</h3>
              <div class="mt-3 space-y-6 text-sm text-gray-500" v-html="review.content" />
              
            <div class="mt-6 flex items-center text-sm">
              <p class="font-medium text-gray-900">{{ review.author }}</p>

              <div class="ml-4 lg:ml-8">
                <time :datetime="review.datetime" class="ml-4 border-l border-gray-200 pl-4 text-gray-500 lg:ml-0 lg:mt-2 lg:border-0 lg:pl-0">{{ review.date }}</time>
              </div>
              
            </div>
            </div>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

 definePageMeta({
  layout: "main-layout",
  });
  
import { StarIcon } from '@heroicons/vue/20/solid'

const reviews = [
  {
    id: 1,
    title: "Can't say enough good things",
    rating: 5,
    content: `
      <p>I was really pleased with the overall shopping experience. My order even included a little personal, handwritten note, which delighted me!</p>
      <p>The product quality is amazing, it looks and feel even better than I had anticipated. Brilliant stuff! I would gladly recommend this store to my friends. And, now that I think of it... I actually have, many times!</p>
    `,
    author: 'Risako M',
    date: 'May 16, 2021',
    datetime: '2021-01-06',
    imageSrc: 'https://allorabd.com/wp-content/uploads/2024/01/DSC_0382.jpg',
  },
  // More reviews...
]
</script>