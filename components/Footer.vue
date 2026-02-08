<!-- components/Footer.vue -->
<template>
    <footer class="bg-navy-950 border-t border-white/10 pt-16 pb-8">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-12 mb-12">
                <!-- Brand Section -->
                <div class="space-y-4">
                    <div class="flex items-center space-x-2 text-emerald-400">
                        <i class="fa fa-code text-2xl"></i>
                        <span class="text-xl font-bold text-white tracking-tight">David Orji</span>
                    </div>
                    <p class="text-slate-400 max-w-xs">
                        {{ $t('footer.brandDescription') }}
                    </p>

                    <!-- Social Links -->
                    <div class="space-y-3">
                        <p class="text-slate-500 text-sm font-medium">{{ $t('footer.connectWith') }}</p>
                        <div class="flex flex-wrap gap-3">
                            <a v-for="social in socialLinks" :key="social.name" :href="social.url" target="_blank"
                                :title="social.name"
                                :class="['text-slate-400 transition-all duration-200 hover:scale-110', social.color]">
                                <i :class="social.icon" class="text-xl"></i>
                            </a>
                        </div>
                    </div>

                    <!-- Blog Links -->
                    <div class="space-y-3">
                        <p class="text-slate-500 text-sm font-medium">{{ $t('footer.readBlogs') }}</p>
                        <div class="flex gap-3">
                            <a v-for="blog in blogLinks" :key="blog.name" :href="blog.url" target="_blank"
                                :title="blog.name"
                                :class="['text-slate-400 transition-all duration-200 hover:scale-110', blog.color]">
                                <i v-if="blog.icon" :class="blog.icon" class="text-xl"></i>
                                <span v-else v-html="blog.svgIcon" class="inline-block w-5 h-5"></span>
                            </a>
                        </div>
                    </div>
                </div>

                <!-- Quick Links -->
                <div>
                    <h3 class="text-white font-semibold mb-4">{{ $t('footer.quickLinks') }}</h3>
                    <ul class="space-y-2">
                        <li><a href="#home" class="text-slate-400 hover:text-emerald-400 transition-colors">{{
                                $t('header.nav.home') }}</a>
                        </li>
                        <li><a href="#about" class="text-slate-400 hover:text-emerald-400 transition-colors">{{
                                $t('header.nav.about') }}</a>
                        </li>
                        <li><a href="#projects" class="text-slate-400 hover:text-emerald-400 transition-colors">{{
                                $t('header.nav.projects') }}</a></li>
                        <li><a href="#contact" class="text-slate-400 hover:text-emerald-400 transition-colors">{{
                                $t('header.nav.contact') }}</a></li>
                    </ul>
                </div>

                <!-- Tech Stack -->
                <div>
                    <h3 class="text-white font-semibold mb-4">{{ $t('footer.techStack') }}</h3>
                    <ul class="space-y-2">
                        <li class="text-slate-400 flex items-center gap-2">
                            <i class="fab fa-node-js text-emerald-400"></i>
                            <span>Node.js & Express</span>
                        </li>
                        <li class="text-slate-400 flex items-center gap-2">
                            <i class="fab fa-react text-emerald-400"></i>
                            <span>React & Next.js</span>
                        </li>
                        <li class="text-slate-400 flex items-center gap-2">
                            <i class="fab fa-vuejs text-emerald-400"></i>
                            <span>Vue.js & Nuxt.js</span>
                        </li>
                        <li class="text-slate-400 flex items-center gap-2">
                            <i class="fa fa-database text-emerald-400"></i>
                            <span>MongoDB & PostgreSQL</span>
                        </li>
                        <li class="text-slate-400 flex items-center gap-2">
                            <i class="fab fa-docker text-emerald-400"></i>
                            <span>Docker & AWS</span>
                        </li>
                    </ul>
                </div>
            </div>

            <!-- Bottom Section -->
            <div class="border-t border-white/10 pt-8 flex flex-col md:flex-row items-center justify-between gap-4">
                <p class="text-slate-500 text-sm">
                    © {{ new Date().getFullYear() }} David Orji. {{ $t('footer.rights') }}
                </p>
            </div>
        </div>
    </footer>
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
    },
    {
        name: 'Twitter',
        url: 'https://x.com/sir_dayvido',
        icon: 'fab fa-twitter',
        color: 'hover:text-blue-400'
    }
];

const blogLinks = [
    {
        name: 'Medium',
        url: 'https://medium.com/@orjidavid0063',
        icon: 'fab fa-medium',
        color: 'hover:text-green-400',
        svgIcon: null
    },
    {
        name: 'Hashnode',
        url: 'https://hashnode.com/@orjidavid',
        icon: null,
        color: 'hover:text-blue-500',
        svgIcon: '<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M22.351 8.019l-6.37-6.37a5.63 5.63 0 0 0-7.962 0l-6.37 6.37a5.63 5.63 0 0 0 0 7.962l6.37 6.37a5.63 5.63 0 0 0 7.962 0l6.37-6.37a5.63 5.63 0 0 0 0-7.962zM12 15.953a3.953 3.953 0 1 1 0-7.906 3.953 3.953 0 0 1 0 7.906z"/></svg>'
    }
];
</script>
