<!-- components/ProjectsSection.vue -->
<template>
    <section id="projects" class="py-24 bg-navy-900 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold text-white mb-4">{{ $t('projects.title') }}</h2>
                <p class="text-slate-400 max-w-2xl mx-auto">
                    {{ $t('projects.subtitle') }}
                </p>
            </div>

            <div class="flex flex-wrap justify-center gap-2 mb-12">
                <button v-for="filter in filters" :key="filter" @click="activeFilter = filter" :class="[
                    'px-4 py-2 rounded-full text-sm font-medium transition-all duration-200',
                    activeFilter === filter
                        ? 'bg-emerald-500 text-white shadow-lg shadow-emerald-500/25'
                        : 'bg-navy-800 text-slate-400 hover:text-white hover:bg-navy-700'
                ]">
                    {{ $t(`projects.filters.${filterKeys[filter]}`) }}
                </button>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <ProjectCard v-for="project in displayedProjects" :key="project.id" :project="project" />
            </div>

            <!-- View More/Less Button -->
            <div v-if="filteredProjects.length > 6" class="text-center mt-12">
                <button @click="showAll = !showAll"
                    class="px-6 py-3 text-sm font-medium text-white bg-emerald-500 rounded-full hover:bg-emerald-600 transition-all duration-200 shadow-lg shadow-emerald-500/25">
                    <i :class="showAll ? 'fa fa-chevron-up' : 'fa fa-chevron-down'" class="mr-2"></i>
                    {{ showAll ? $t('projects.viewLess') : $t('projects.viewMore') }}
                </button>
            </div>
        </div>
    </section>
</template>

<script setup>
const activeFilter = ref('All');
const showAll = ref(false);
const filters = ['All', 'Web App', 'Mobile', 'E-commerce'];

// Map filter names to translation keys
const filterKeys = {
    'All': 'all',
    'Web App': 'webApp',
    'Mobile': 'mobile',
    'E-commerce': 'ecommerce'
};

const allProjects = [
    {
        id: 1,
        title: 'TravelTube',
        description: 'TravelTube connects travellers with stories, tools, and experiences from across the world.',
        image: '/assets/images/traveltube.png',
        technologies: ['Nuxt.js', 'TypeScript', 'Pinia', 'MongoDB'],
        github: '#',
        demo: 'https://traveltube.io',
        category: 'Web App'
    },
    {
        id: 2,
        title: 'TravelTube Services',
        description: 'Register Your Business on TravelTube Services Platform to Showcase your services to millions of travelers worldwide.',
        image: '/assets/images/services.png',
        technologies: ['Nuxt.js', 'TypeScript', 'Pinia', 'MongoDB'],
        github: '#',
        demo: 'https://services.traveltube.io',
        category: 'Web App'
    },
    {
        id: 3,
        title: 'TravelTube Restaurants',
        description: 'TravelTube Restaurants is an all-in-one hospitality platform combining QR ordering, POS, and in-restaurant entertainment.',
        image: '/assets/images/restaurant.png',
        technologies: ['Nuxt.js', 'TypeScript', 'Pinia', 'MongoDB'],
        github: '#',
        demo: 'https://restaurants.traveltube.io',
        category: 'Web App'
    },
    {
        id: 4,
        title: 'TravelTube Creators',
        description: 'A platform to upload, manage, and showcase your travel content. Connect with audiences worldwide and grow your creator journey.',
        image: '/assets/images/creators.png',
        technologies: ['Nuxt.js', 'TypeScript', 'Pinia', 'MongoDB'],
        github: '#',
        demo: 'https://creators.traveltube.io',
        category: 'Web App'
    },
    {
        id: 5,
        title: 'MySchool Research',
        description: 'Publish, discover, and collaborate on academic work with MySchool Research.',
        image: '/assets/images/schoolresearch.png',
        technologies: ['Nuxt.js', 'TypeScript', 'Pinia', 'MongoDB'],
        github: '#',
        demo: 'https://myschoolresearch.org',
        category: 'Web App'
    },
    {
        id: 6,
        title: 'DCI WIKI',
        description: 'Open system for registering and protecting research, creative content, and cultural heritage.',
        image: '/assets/images/dciwiki.png',
        technologies: ['Nuxt.js', 'TypeScript', 'Pinia', 'MongoDB'],
        github: '#',
        demo: 'https://dci.wiki',
        category: 'Web App'
    },
    {
        id: 7,
        title: 'MySchool Academy',
        description: 'MySchool Academy is dedicated to making STEM education practical and accessible for African students.',
        image: '/assets/images/schoolacademy.png',
        technologies: ['Nuxt.js', 'TypeScript', 'Pinia', 'MongoDB'],
        github: '#',
        demo: 'https://myschoolacademy.org',
        category: 'Web App'
    },
    {
        id: 8,
        title: 'Largo Integrated',
        description: 'Dynamic Nigerian enterprise offering integrated business solutions across multiple sectors.',
        image: '/assets/images/largo.png',
        technologies: ['Next.js', 'TypeScript', 'Tailwind CSS', 'Framer Motion'],
        github: 'https://github.com/Dayvid0063',
        demo: 'https://www.largointegrated.com',
        category: 'Web App'
    },
    {
        id: 9,
        title: 'QUICK-CART',
        description: 'Multi-vendor e-commerce mobile application for browsing products, managing cart and making purchases.',
        image: '/assets/images/qcImg.png',
        technologies: ['React Native', 'Express.js', 'Prisma', 'MongoDB'],
        github: 'https://github.com/Dayvid0063',
        demo: 'https://youtu.be/o5a2ZY5OSCg?si=UiTzs_EH7zrr3WHU',
        category: 'Mobile'
    },
    {
        id: 10,
        title: 'BLESSED BALES AND BUNDLE',
        description: 'Website designed for customers to shop for Fabrics with an intuitive interface and seamless shopping experience.',
        image: '/assets/images/blessedbb.png',
        technologies: ['Next.js', 'TypeScript', 'Shadcn', 'Tailwind CSS'],
        github: 'https://github.com/Dayvid0063',
        demo: 'https://blessed-bales-and-bundles.vercel.app',
        category: 'E-commerce'
    },
    {
        id: 11,
        title: 'MoveIt',
        description: 'E-commerce mobile application for browsing and booking car rentals with payment integration.',
        image: '/assets/images/moveit.png',
        technologies: ['React Native', 'Next.js', 'Prisma', 'PostgreSQL'],
        github: 'https://github.com/Dayvid0063',
        demo: 'https://youtu.be/u_2vPF3azbU',
        category: 'E-commerce'
    },
    {
        id: 12,
        title: 'Med-Equip Solutions',
        description: 'Trusted partner in medical equipment solutions, dedicated to improving healthcare delivery worldwide.',
        image: '/assets/images/med-equip.png',
        technologies: ['Next.js', 'TypeScript', 'Shadcn', 'Tailwind CSS'],
        github: 'https://github.com/Dayvid0063',
        demo: 'https://medical-equip.vercel.app',
        category: 'E-commerce'
    },
    {
        id: 13,
        title: 'Rivers Youth Hub',
        description: 'Comprehensive digital platform providing skill development, job placement, and entrepreneurship support.',
        image: '/assets/images/riversyouth-hub.png',
        technologies: ['Next.js', 'TypeScript', 'Shadcn', 'Tailwind CSS'],
        github: 'https://github.com/Dayvid0063',
        demo: 'https://www.nycnriversstate.com',
        category: 'Web App'
    },
    {
        id: 14,
        title: 'LOCALBIZ CONNECT',
        description: 'Your go-to online solution for discovering and supporting local businesses in your neighborhood.',
        image: '/assets/images/localbiz.png',
        technologies: ['React.js', 'Express.js', 'MongoDB', 'Mongoose'],
        github: 'https://github.com/Dayvid0063',
        demo: 'https://youtu.be/ujbGe3AXheg?si=RLacGZJW_m-75uLe',
        category: 'Web App'
    }
];

// Filter projects based on active filter
const filteredProjects = computed(() => {
    if (activeFilter.value === 'All') {
        return allProjects;
    }
    return allProjects.filter(project => project.category === activeFilter.value);
});

// Display only first 6 projects or all based on showAll state
const displayedProjects = computed(() => {
    if (showAll.value) {
        return filteredProjects.value;
    }
    return filteredProjects.value.slice(0, 6);
});

// Reset showAll when filter changes
watch(activeFilter, () => {
    showAll.value = false;
});
</script>
