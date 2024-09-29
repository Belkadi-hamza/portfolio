<template>
    <section class="text-white mt-20" id="services">
        <div class="px-4 xl:pl-16">
            <h2 class="text-4xl font-bold text-white mb-4">My Services</h2>
        </div>
        <div class="px-4 xl:px-16">
            <Carousel v-bind="settings" :breakpoints="breakpoints">
                <Slide v-for="service in services" :key="service.id">
                    <div class="px-8 py-12 rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641] mx-4">
                    <div class="carousel__item p-4">
                        <div class="mx-auto h-24 w-24 text-center xl:h-28 xl:w-28">
                            <div>
                                <img :src="service.icon" alt="service icon" height="100%" width="100%">
                            </div>
                        </div>
                        <div class="text-center">
                            <h3
                                class="pt-8 text-lg font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl">
                                {{ service.name }}
                            </h3>
                            <p class="text-grey pt-4 text-sm group-hover:text-white md:text-base">
                                {{ service.description }}
                            </p>
                        </div>
                    </div>
                </div>
                </Slide>
                <template #addons>
                    <Navigation />
                </template>
            </Carousel>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';
import { Carousel, Navigation, Slide } from 'vue3-carousel';
import 'vue3-carousel/dist/carousel.css';
import GoogleCode from './../assets/services/icons8-google-code-50.png'
import WebDesign from './../assets/services/icons8-web-design-50.png'
import Api from './../assets/services/icons8-api-50.png'
import DatabaseManagement from './../assets/services/icons8-database-50.png'
import UX from './../assets/services/icons8-ux-design-68.png'
import Frontend from './../assets/services/icons8-front-end-50.png'
import Backend from './../assets/services/icons8-backend-development-100.png'
import CloudServices from './../assets/services/icons8-cloud-computing-50.png'
import SEO from './../assets/services/icons8-seo-50.png'
import CMS from './../assets/services/icons8-content-management-48.png'
//Carousel settings
const settings = ref({
    itemsToShow: 1,
    snapAlign: "center",
})

//Breakpoints
const breakpoints = ref({
    700: {
        itemsToShow: 2.5,
        snapAlign: 'center',
    },
    1024: {
        itemsToShow: 3,
        snapAlign: 'start'
    }
})

const services = ref([
    {
        id: 1,
        icon: GoogleCode,
        name: 'Web Development',
        description: 'Building robust and scalable web applications using modern frameworks and technologies.'
    },
    {
        id: 2,
        icon: WebDesign,
        name: 'Web Design',
        description: 'Creating visually appealing and user-friendly designs tailored to your brand and audience.'
    },
    {
        id: 3,
        icon: Api,
        name: 'API Development',
        description: 'Developing RESTful and GraphQL APIs for seamless integration with frontend applications.'
    },
    {
        id: 4,
        icon: DatabaseManagement,
        name: 'Database Management',
        description: 'Designing and managing efficient database systems for data integrity and performance.'
    },
    {
        id: 5,
        icon: UX,
        name: 'User Experience (UX) Design',
        description: 'Conducting user research and usability testing to enhance user satisfaction and engagement.'
    },
    {
        id: 6,
        icon: Frontend,
        name: 'Frontend Development',
        description: 'Creating responsive and interactive user interfaces using HTML, CSS, and JavaScript frameworks.'
    },
    {
        id: 7,
        icon: Backend,
        name: 'Backend Development',
        description: 'Building server-side logic and database interactions using languages like PHP, Node.js, or Java.'
    },
    {
        id: 8,
        icon: CloudServices,
        name: 'Cloud Services',
        description: 'Leveraging cloud platforms like AWS and Azure for deployment, storage, and scalability.'
    },
    {
        id: 9,
        icon: SEO,
        name: 'Search Engine Optimization (SEO)',
        description: 'Optimizing websites to improve visibility and ranking on search engines.'
    },
    {
        id: 10,
        icon: CMS,
        name: 'Content Management System (CMS) Development',
        description: 'Implementing custom CMS solutions for easy content updates and management.'
    },
])
</script>
<style>
.carousel__prev,
.carousel__next {
    color: white !important;
}
</style>