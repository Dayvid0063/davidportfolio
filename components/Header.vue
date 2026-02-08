<!-- components/Header.vue -->
<template>
    <header
        class="fixed top-0 left-0 right-0 z-40 transition-all duration-300 bg-navy-900/95 backdrop-blur-md border-b border-white/5 py-3">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between">
                <a href="#home"
                    class="flex items-center space-x-2 text-emerald-400 hover:text-emerald-300 transition-colors">
                    <i class="fa fa-code text-2xl"></i>
                    <span class="text-xl font-bold text-white tracking-tight">David Orji</span>
                </a>

                <nav class="hidden md:flex items-center space-x-8">
                    <a href="#home"
                        :class="activeSection === 'home' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                        class="text-sm font-medium transition-colors duration-200">{{ $t('header.nav.home') }}</a>
                    <a href="#about"
                        :class="activeSection === 'about' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                        class="text-sm font-medium transition-colors duration-200">{{ $t('header.nav.about') }}</a>
                    <a href="#projects"
                        :class="activeSection === 'projects' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                        class="text-sm font-medium transition-colors duration-200">{{ $t('header.nav.projects') }}</a>
                    <a href="#contact"
                        :class="activeSection === 'contact' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                        class="text-sm font-medium transition-colors duration-200">{{ $t('header.nav.contact') }}</a>

                    <!-- Language Switcher -->
                    <div class="relative">
                        <button @click="toggleLanguageMenu"
                            class="px-3 py-2 text-sm font-medium text-slate-300 hover:text-white transition-colors duration-200 flex items-center gap-2">
                            <i class="fa fa-globe"></i>
                            <span>{{ currentLocale.toUpperCase() }}</span>
                            <i :class="languageMenuOpen ? 'fa fa-chevron-up' : 'fa fa-chevron-down'"
                                class="text-xs"></i>
                        </button>

                        <!-- Language Dropdown -->
                        <div v-if="languageMenuOpen"
                            class="absolute right-0 mt-2 w-40 bg-navy-800 border border-white/10 rounded-lg shadow-xl overflow-hidden z-50">
                            <button v-for="locale in availableLocales" :key="locale.code"
                                @click="switchLanguage(locale.code)" :class="[
                                    'w-full px-4 py-2.5 text-left text-sm transition-colors duration-200',
                                    currentLocale === locale.code
                                        ? 'bg-emerald-500/20 text-emerald-400'
                                        : 'text-slate-300 hover:bg-navy-700 hover:text-white'
                                ]">
                                {{ locale.name }}
                            </button>
                        </div>
                    </div>

                    <a href="https://drive.google.com/drive/folders/128GMZY7feBsZsB4WEIt2SeW-qIb4m50k?usp=sharing"
                        target="_blank"
                        class="px-4 py-2 text-sm font-medium text-navy-900 bg-emerald-400 rounded-full hover:bg-emerald-300 transition-colors">{{
                            $t('header.nav.resume') }}</a>
                </nav>

                <button @click="toggleMenu" class="md:hidden p-2 text-slate-300 hover:text-white">
                    <i class="fa fa-bars text-xl"></i>
                </button>
            </div>

            <!-- Mobile Menu -->
            <div v-if="menuOpen" class="md:hidden mt-4 py-4 space-y-3">
                <a href="#home"
                    :class="activeSection === 'home' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                    class="block text-sm font-medium">{{ $t('header.nav.home') }}</a>
                <a href="#about"
                    :class="activeSection === 'about' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                    class="block text-sm font-medium">{{ $t('header.nav.about') }}</a>
                <a href="#projects"
                    :class="activeSection === 'projects' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                    class="block text-sm font-medium">{{ $t('header.nav.projects') }}</a>
                <a href="#contact"
                    :class="activeSection === 'contact' ? 'text-emerald-400' : 'text-slate-300 hover:text-white'"
                    class="block text-sm font-medium">{{ $t('header.nav.contact') }}</a>

                <!-- Mobile Language Switcher -->
                <div class="pt-2 border-t border-white/10">
                    <p class="text-xs text-slate-500 mb-2 px-2">Language</p>
                    <div class="space-y-1">
                        <button v-for="locale in availableLocales" :key="locale.code"
                            @click="switchLanguage(locale.code)" :class="[
                                'w-full px-4 py-2 text-left text-sm transition-colors duration-200 rounded-lg',
                                currentLocale === locale.code
                                    ? 'bg-emerald-500/20 text-emerald-400'
                                    : 'text-slate-300 hover:bg-navy-700 hover:text-white'
                            ]">
                            {{ locale.name }}
                        </button>
                    </div>
                </div>

                <a href="https://drive.google.com/drive/folders/128GMZY7feBsZsB4WEIt2SeW-qIb4m50k?usp=sharing"
                    target="_blank"
                    class="block px-4 py-2 text-sm font-medium text-navy-900 bg-emerald-400 rounded-full hover:bg-emerald-300 transition-colors text-center">{{
                        $t('header.nav.resume') }}</a>
            </div>
        </div>
    </header>
</template>

<script setup>
const { locale, locales, setLocale } = useI18n();
const menuOpen = ref(false);
const activeSection = ref('home');
const languageMenuOpen = ref(false);

const currentLocale = computed(() => locale.value);
const availableLocales = computed(() => locales.value);

const toggleMenu = () => {
    menuOpen.value = !menuOpen.value;
};

const toggleLanguageMenu = () => {
    languageMenuOpen.value = !languageMenuOpen.value;
};

const switchLanguage = async (newLocale) => {
    await setLocale(newLocale);
    languageMenuOpen.value = false;
    menuOpen.value = false; // Close mobile menu if open
};

// Close language menu when clicking outside
onMounted(() => {
    const handleClickOutside = (event) => {
        if (languageMenuOpen.value && !event.target.closest('.relative')) {
            languageMenuOpen.value = false;
        }
    };

    document.addEventListener('click', handleClickOutside);

    onUnmounted(() => {
        document.removeEventListener('click', handleClickOutside);
    });
});

// Simple scroll-based active section tracking
onMounted(() => {
    const updateActiveSection = () => {
        const sections = ['home', 'about', 'projects', 'contact'];
        const scrollPosition = window.scrollY + 150; // Offset for header

        for (const sectionId of sections) {
            const element = document.getElementById(sectionId);
            if (element) {
                const { offsetTop, offsetHeight } = element;
                if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
                    activeSection.value = sectionId;
                    break;
                }
            }
        }
    };

    // Update on scroll
    window.addEventListener('scroll', updateActiveSection);
    // Update on load
    updateActiveSection();

    // Cleanup
    onUnmounted(() => {
        window.removeEventListener('scroll', updateActiveSection);
    });
});
</script>
