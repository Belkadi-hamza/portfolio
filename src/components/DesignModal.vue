<template>
  <div class="grid grid-cols-3">
    <div class="col-span-2">
      <!-- ScrollSpy container -->
      <div data-twe-spy="scroll" data-twe-target="#scrollspy1" data-twe-offset="0" class="relative h-96 overflow-auto">
        <!-- Scrollable sections -->
        <section id="example-1">
          <div class="fixed inset-0 flex items-center justify-center z-50">
            <div class="fixed inset-0 bg-black opacity-50" @click="closeModal"></div>
            <div class="bg-white rounded-lg shadow-lg overflow-hidden max-w-lg w-full z-10">
              <div class="relative p-6">

                <button class="absolute top-4 right-4 text-gray-500 hover:text-gray-800" @click="closeModal">
                  <img :src="closeIcon" alt="Close" class="w-5 h-5">
                </button>

                <div class="text-center mb-6">
                  <h2 class="text-3xl font-semibold text-gray-800">{{ project.title }}</h2>
                  <p class="text-gray-600 mt-2 text-sm">{{ project.description }}</p>

                  <div class="flex items-center gap-3 pt-4 flex-wrap justify-center">
                    <div v-for="(technologie, index) in project.technologies" :key="index">
                      <span class="technology-tag">{{ technologie }}</span>
                    </div>
                  </div>
                </div>

                <!-- Carousel -->
                <Carousel v-bind="settings" :breakpoints="breakpoints">
                  <Slide v-for="(img, index) in project.image" :key="index">
                    <div class="carousel-horizontal-container">
                      <div class="carousel-horizontal">
                        <img :src="img" alt="Project Image" class="w-full h-auto object-cover rounded-lg">
                      </div>
                    </div>
                  </Slide>
                  <template #addons>
                    <Navigation />
                  </template>
                </Carousel>

                <div class="flex justify-center space-x-4 mt-6">
                  <a v-if="project.gitURL" :href="project.gitURL" target="_blank"
                    class="px-5 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition duration-200 font-medium">
                    Voir sur GitHub
                  </a>
                  <a v-if="project.webURL" :href="project.webURL" target="_blank"
                    class="px-5 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 transition duration-200 font-medium">
                    Démo en Direct
                  </a>
                </div>
              </div>
            </div>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Carousel, Navigation, Slide } from 'vue3-carousel';
import closeIcon from './../assets/icons/multiply-icon.svg';

const props = defineProps({
  project: {
    type: Object,
    required: true
  }
});

const emit = defineEmits(['close']);

const closeModal = () => {
  emit('close');
};

// Initialize ScrollSpy from tw-elements
import { ScrollSpy, initTWE } from "tw-elements";
initTWE({ ScrollSpy });
</script>

<style scoped>
/* Modal Styles */
.carousel__prev,
.carousel__next {
  color: #333 !important;
}

/* Title and text styling */
h2 {
  color: #111827;
}

p {
  color: #6b7280;
}

/* Professional tag styling for technologies */
.technology-tag {
  background-color: #f59e0b;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 9999px;
  font-size: 0.875rem;
  font-weight: 500;
  margin-bottom: 0.5rem;
  transition: transform 0.3s;
}

.technology-tag:hover {
  transform: scale(1.05);
}

/* Button styling */
a {
  font-size: 1rem;
}

a:hover {
  transform: translateY(-2px);
  transition: transform 0.2s ease-in-out;
}

/* Image styles */
img {
  border-radius: 8px;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .technology-tag {
    font-size: 0.75rem;
    padding: 0.375rem 0.75rem;
  }

  .px-5 {
    padding-left: 1rem;
    padding-right: 1rem;
  }
}
</style>
