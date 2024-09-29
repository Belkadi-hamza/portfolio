<template>
    <section class="text-white mt-20" id="projects">
        <div class="px-4 xl:pl-16">
            <div class="mb-4 md:flex md:justify-between xl:pr-16">
                <h2 class="text-4xl font-bold text-white">My Latest Projects</h2>
                <div class="flex space-x-4 mb-4 mt-5 md:mt-0">
                    <button class="hover:text-primary" v-for="category in ['all', 'web development', 'Descktop Development']"
                        :key="category" @click="selectedCategory = category">
                        {{ category }}
                    </button>
                </div>
            </div>
            <ul class="px-4 sm:py-16 xl:pr-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3"
                data-aos="fade-right">
                <li v-for="project in filteredProjects" :key="project.id">
                    <div class="h-52 md:h-[24rem] rounded-t-xl relative group"
                        :style="{ backgroundImage: `url(${project.logo})`, backgroundSize: 'cover' }">
                        <div
                            class="overlay items-center justify-center absolute top-0 left-0 w-full h-full bg-[#181818] bg-opacity-0 hidden group-hover:flex group-hover:bg-opacity-80 transition-all duration-500">
                            <!-- <a class="h-14 w-14 mr-2 border-2 relative rounded-full border-[#ADB7BE] hover:border-white group/link"
                                :href="project.webURL" target="_blank">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" aria-hidden="true"
                                    class="h-10 w-10 text-[#ADB7BE] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 cursor-pointer group-hover/link:text-white">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M17.25 6.75 22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3-4.5 16.5" />
                                </svg>
                            </a> -->
                            <a class="h-14 w-14 border-2 relative rounded-full border-[#ADB7BE] hover:border-white group/link"
                                @click.prevent="showProjectDetails(project)">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" aria-hidden="true"
                                    class="h-10 w-10 text-[#ADB7BE] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 cursor-pointer group-hover/link:text-white">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M2.036 12.322a1.012 1.012 0 0 1 0-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178Z" />
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z" />
                                </svg>
                            </a>
                        </div>
                    </div>
                    <div class="text-white rounded-b-xl mt-3 bg-[#111a3e] shadow-lg border border-[#1f1641] py-6 px-4">
                        <h3 class="text-lg font-semibold uppercase lg:text-xl">
                            {{ project.title }}
                        </h3>
                        <!-- <p class="text-[#ADB7BE]">{{ project.description }}</p> -->
                        <div class="flex flex-wrap p-2.5">
                            <div v-for="technology in project.technologies" :key="technology"
                                class="text-center ml-1 mt-1 rounded-3xl bg-[#111827]"
                                style="box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1); border: 1px solid #111827;backdrop-filter: blur(9px);-webkit-backdrop-filter: blur(9px);">
                                <p class="px-1 py-2">{{ technology }}</p>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </div>
        <!-- DesignModal Component -->
        <DesignModal v-if="isModalVisible" :project="selectedProject" @close="isModalVisible = false" />
    </section>
</template>

<script setup>
import { ref, computed } from 'vue';
import DesignModal from './DesignModal.vue'; // Import the modal component

import chatBootLogo from './../assets/project/chatBoot/logo.jpg';
import chatboot from './../assets/project/chatBoot/chatBoot.jpg';

import tkdLogo from './../assets/project/tkd/logo.jpg';
import tkd from './../assets/project/tkd/tkd.jpg';

import snrtLogo from './../assets/project/snrt/logo.png';
import snrt from './../assets/project/snrt/snrt.jpg';

import bibLogo from './../assets/project/bib/logo.jpg';
import bib from './../assets/project/bib/bib.jpg';

// Project data
const Projects = ref([
    {
        id: 1,
        category: 'Web Development',
        logo: chatBootLogo,
        image: [
            chatboot,
        ],
        title: 'Chat Bot',
        description: 'Developed a chatbot utilizing HTML, CSS, JavaScript, and Python to provide users with instant responses and support.',
        technologies: ['HTML', 'CSS', 'JavaScript', 'Python'],
        gitURL: '', // Add GitHub URL if available
        webURL: '' // Add live demo URL if available
    },
    {
        id: 2,
        category: 'Descktop Development',
        logo: tkdLogo,
        image: [tkd],
        title: 'Taekwondo ScoreMaster',
        description: 'Managed Taekwondo matches with a Java-based system and integrated scoring algorithms to streamline competition management.',
        technologies: ['Java', 'JavaFX'],
        gitURL: '', // Add GitHub URL if available
        webURL: '' // Add live demo URL if available
    },
    {
        id: 3,
        category: 'Web Development',
        logo: snrtLogo,
        image: [snrt],
        title: 'Digital Media Management System',
        description: 'Developed during an internship at SNRT, this system manages digitization and tracks operations using a comprehensive backend.',
        technologies: ['HTML', 'CSS', 'Bootstrap', 'JavaScript', 'Vue.js', 'PHP', 'Laravel', 'MySQL'],
        gitURL: '', // Add GitHub URL if available
        webURL: '' // Add live demo URL if available
    },
    {
        id: 4,
        category: 'Web Development',
        logo: bibLogo,
        image: [bib],
        title: 'Commercial Site with Digital Library',
        description: 'Created a commercial site integrating a digital library and managing backend functionalities for a seamless user experience.',
        technologies: ['HTML', 'CSS', 'Bootstrap', 'JavaScript', 'Vue.js', 'Three.js', 'PHP', 'Laravel', 'MySQL'],
        gitURL: '', // Add GitHub URL if available
        webURL: '' // Add live demo URL if available
    }
]);

// State to manage selected category and filtered projects
const selectedCategory = ref('all');
const filteredProjects = computed(() => {
    if (selectedCategory.value === 'all') {
        return Projects.value;
    }
    return Projects.value.filter(project => project.category.toLowerCase() === selectedCategory.value.toLowerCase());
});

// State for selected project and modal visibility
const selectedProject = ref(null);
const isModalVisible = ref(false);

// Method to show project details in the modal
const showProjectDetails = (project) => {
    selectedProject.value = project;
    isModalVisible.value = true;
};
</script>

<style scoped>
/* Add any additional styles here */
</style>