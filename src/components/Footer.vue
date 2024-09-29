<template>
    <footer class="mt-8 border z-10 border-t-[#33353F] border-l-transparent border-r-transparent text-white bg-[#111a3e]">
        <div class="container p-6 md:p-12 flex flex-col md:flex-row justify-between items-center">
            <div class="text-white text-2xl md:text-3xl font-bold">BELKADI</div>
            <span class="text-sm md:text-base mt-2 md:mt-0">© 2024 Copyright: Belkadi Hamza</span>
            <div class="flex items-center gap-3 pt-4 flex-col sm:flex-row sm:w-max sm:mx-auto lg:mx-0">
                <a :href="linkedinURL" target="_blank" class="social-link">
                    <img :src="linkedin" alt="LinkedIn" class="social-icon">
                </a>
                <a :href="githubURL" target="_blank" class="social-link">
                    <img :src="github" alt="GitHub" class="social-icon">
                </a>
                <a :href="instagramURL" target="_blank" class="social-link">
                    <img :src="instagram" alt="Instagram" class="social-icon">
                </a>
            </div>
        </div>
    </footer>
</template>

<script setup>
import AOS from 'aos';
import linkedin from './../assets/icons/linkedin.svg';
import github from './../assets/icons/github.svg';
import instagram from './../assets/icons/instagram.svg';

import 'aos/dist/aos.css';

const linkedinURL = "https://www.linkedin.com/in/hamza-belkadi-81a756292/";
const githubURL = "https://github.com/Belkadi-hamza";
const instagramURL = "https://www.instagram.com/belkadi.hamza.391?igsh=OGRuMjE2dmVxaGh1";
AOS.init();
</script>

<style scoped>
.container {
    max-width: 1200px; /* Max width for larger screens */
    margin: 0 auto; /* Center the container */
}

.social-link {
    border: 2px solid #f59e0b; /* Adjusted border color */
    border-radius: 50px;
    padding: 10px;
    transition: background-color 0.3s, transform 0.3s; /* Add transition for effects */
    display: inline-flex; /* Flexbox for centering */
    justify-content: center; /* Center the icon */
    align-items: center; /* Center the icon */
}

.social-link:hover {
    transform: translateY(-2px); /* Slight lift effect */
}

.social-icon {
    width: 24px; /* Adjust icon size */
    height: 24px; /* Adjust icon size */
}

/* Responsive styles */
@media (max-width: 768px) {
    .container {
        padding: 20px; /* Adjust padding for mobile */
    }

    .text-2xl {
        font-size: 1.5rem; /* Adjust text size for smaller screens */
    }

    .text-sm {
        font-size: 0.875rem; /* Adjust copyright text size */
    }

    .social-link {
        padding: 8px; /* Adjust padding for social links */
    }

    .social-icon {
        width: 20px; /* Adjust icon size for smaller screens */
        height: 20px; /* Adjust icon size for smaller screens */
    }
}
</style>
