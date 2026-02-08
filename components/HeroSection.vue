<!-- components/HeroSection.vue -->
<template>
    <section id="home" class="relative min-h-screen flex items-center justify-center pt-20 overflow-hidden">
        <!-- Animated Background -->
        <div class="absolute inset-0 z-0">
            <div class="absolute top-20 left-10 w-72 h-72 bg-teal-500/20 rounded-full blur-[100px] animate-pulse-slow">
            </div>
            <div class="absolute bottom-20 right-10 w-96 h-96 bg-emerald-500/20 rounded-full blur-[100px] animate-pulse-slow"
                style="animation-delay: 1000ms;"></div>
            <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-[500px] h-[500px] bg-emerald-400/10 rounded-full blur-[120px] animate-pulse-slow"
                style="animation-delay: 2000ms;"></div>
        </div>

        <!-- Floating Particles -->
        <FloatingParticles />

        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center w-full">
            <div class="space-y-8 animate-fade-in-up">
                <!-- Main Heading -->
                <div>
                    <h1 class="text-4xl sm:text-5xl md:text-7xl font-bold tracking-tight text-white mb-4">
                        {{ $t('hero.greeting') }} <span
                            class="text-transparent bg-clip-text bg-gradient-to-r from-emerald-400 to-teal-400">{{
                            $t('hero.name') }}</span>
                    </h1>
                    <h2 class="text-2xl sm:text-3xl md:text-5xl font-bold tracking-tight">
                        <span
                            class="text-transparent bg-clip-text bg-gradient-to-r from-emerald-400 via-teal-400 to-emerald-500">
                            {{ $t('hero.title') }}
                        </span>
                    </h2>
                </div>

                <!-- CTA Buttons -->
                <div class="flex flex-col sm:flex-row items-center justify-center gap-4 pt-8">
                    <a href="#projects"
                        class="inline-flex items-center justify-center rounded-lg font-medium transition-all duration-200 bg-emerald-500 text-white hover:bg-emerald-600 shadow-lg shadow-emerald-500/25 px-8 py-3.5 text-lg w-full sm:w-auto">
                        {{ $t('hero.viewProjects') }}
                        <i class="fa fa-arrow-right ml-2"></i>
                    </a>
                    <a href="https://drive.google.com/drive/folders/128GMZY7feBsZsB4WEIt2SeW-qIb4m50k?usp=sharing"
                        target="_blank"
                        class="inline-flex items-center justify-center rounded-lg font-medium transition-all duration-200 bg-transparent border-2 border-emerald-500 text-emerald-400 hover:bg-emerald-500/10 px-8 py-3.5 text-lg w-full sm:w-auto">
                        <i class="fa fa-file-alt mr-2"></i>
                        {{ $t('hero.viewResume') }}
                    </a>
                </div>

                <!-- Social Links -->
                <div class="pt-8">
                    <div class="flex items-center justify-center gap-6">
                        <a v-for="social in socialLinks" :key="social.name" :href="social.url" target="_blank"
                            :title="social.name"
                            :class="['text-slate-400 transition-all duration-200 transform hover:scale-110', social.color]">
                            <i :class="social.icon" class="text-2xl"></i>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
const socialLinks = [
    {
        name: 'GitHub',
        url: 'https://github.com/Dayvid0063',
        icon: 'fab fa-github',
        color: 'hover:text-white'
    },
    {
        name: 'LinkedIn',
        url: 'https://www.linkedin.com/in/david-orji-/',
        icon: 'fab fa-linkedin',
        color: 'hover:text-blue-400'
    }
];
</script>
