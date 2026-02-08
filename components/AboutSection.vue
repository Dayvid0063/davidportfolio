<!-- components/AboutSection.vue -->
<template>
    <section ref="aboutSection" id="about" class="py-24 bg-navy-900 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Centered Title -->
            <h2 class="text-3xl md:text-4xl font-bold text-white mb-12 text-center">{{ $t('about.title') }}</h2>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-start">
                <!-- Left Column - Profile & About -->
                <div class="space-y-6">
                    <div class="flex flex-col sm:flex-row items-center gap-6">
                        <div class="relative flex-shrink-0">
                            <div
                                class="absolute -inset-2 bg-gradient-to-r from-emerald-500 to-teal-500 rounded-2xl blur-md opacity-30">
                            </div>
                            <NuxtImg src="/assets/images/dayv.PNG" alt="Profile"
                                class="relative rounded-2xl shadow-2xl w-32 h-32 sm:w-40 sm:h-40 object-cover object-top" />
                        </div>
                        <div class="flex-1 text-center sm:text-left">
                            <p class="text-slate-400 leading-relaxed">
                                {{ $t('about.bio1') }}
                                <br><br>
                                {{ $t('about.bio2') }}
                            </p>
                        </div>
                    </div>

                    <p class="text-slate-400 leading-relaxed">
                        {{ $t('about.bio3') }}
                    </p>

                    <button @click="showCertifications = true"
                        class="inline-flex items-center justify-center rounded-lg font-medium transition-all duration-200 bg-teal-600 text-white hover:bg-teal-700 shadow-lg shadow-teal-600/25 px-5 py-2.5 text-base">
                        <i class="fa fa-award mr-2"></i>
                        {{ $t('about.viewCertifications') }}
                    </button>
                </div>

                <!-- Right Column - Skills -->
                <div class="space-y-6">
                    <h3 class="text-xl font-semibold text-white">{{ $t('about.technicalProficiency') }}</h3>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div v-for="skill in skills" :key="skill.name" class="space-y-2">
                            <div class="flex justify-between text-sm items-center">
                                <span class="text-slate-300 flex items-center gap-2">
                                    <i :class="skill.icon"></i>
                                    {{ skill.name }}
                                </span>
                                <span class="text-emerald-400 text-xs">{{ skill.level }}%</span>
                            </div>
                            <div class="h-1.5 bg-navy-800 rounded-full overflow-hidden">
                                <div class="h-full bg-gradient-to-r from-emerald-500 to-teal-500 rounded-full transition-all duration-1000 ease-out"
                                    :style="{ width: animatedSkills[skill.name] + '%' }"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Certifications Modal - Compact -->
        <div v-if="showCertifications" @click="showCertifications = false"
            class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/80 backdrop-blur-sm">
            <div @click.stop
                class="bg-navy-800 border border-white/10 rounded-2xl max-w-2xl w-full max-h-[85vh] overflow-y-auto p-6">
                <div class="flex items-center justify-between mb-6">
                    <h3 class="text-xl font-bold text-white">{{ $t('about.certificationsTitle') }}</h3>
                    <button @click="showCertifications = false"
                        class="text-slate-400 hover:text-white transition-colors p-2">
                        <i class="fa fa-times text-lg"></i>
                    </button>
                </div>

                <div class="space-y-3">
                    <a v-for="cert in certifications" :key="cert.id" :href="cert.link" target="_blank"
                        class="block bg-navy-900/50 border border-white/5 rounded-xl p-4 hover:border-emerald-500/30 transition-all duration-300 hover:-translate-y-1 group">
                        <div class="flex items-start gap-3">
                            <div class="text-2xl flex-shrink-0">{{ cert.badge }}</div>
                            <div class="flex-1 min-w-0">
                                <h4
                                    class="text-white font-semibold text-sm mb-1 group-hover:text-emerald-400 transition-colors">
                                    {{ cert.name }}
                                </h4>
                                <p class="text-slate-400 text-xs mb-1">{{ cert.issuer }}</p>
                                <div class="flex items-center justify-between">
                                    <span class="text-slate-500 text-xs">{{ cert.date }}</span>
                                    <i
                                        class="fa fa-external-link-alt text-emerald-400 text-xs opacity-0 group-hover:opacity-100 transition-opacity"></i>
                                </div>
                            </div>
                        </div>
                    </a>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
const showCertifications = ref(false);

// Initialize animated skills with 0% width
const animatedSkills = ref({});

const skills = [
    { name: 'Node.js', level: 80, icon: 'fab fa-node-js', category: 'Backend' },
    { name: 'Express.js', level: 80, icon: 'fa fa-server', category: 'Backend' },
    { name: 'TypeScript', level: 80, icon: 'fa fa-code', category: 'Language' },
    { name: 'Golang', level: 70, icon: 'fa fa-code', category: 'Language' },
    { name: 'React Native', level: 80, icon: 'fab fa-react', category: 'Mobile' },
    { name: 'React', level: 80, icon: 'fab fa-react', category: 'Frontend' },
    { name: 'Next.js', level: 80, icon: 'fa fa-window-maximize', category: 'Frontend' },
    { name: 'Tailwind CSS', level: 80, icon: 'fa fa-palette', category: 'Frontend' },
    { name: 'Figma', level: 80, icon: 'fab fa-figma', category: 'Design' },
    { name: 'AWS', level: 70, icon: 'fab fa-aws', category: 'DevOps' },
    { name: 'Docker', level: 70, icon: 'fab fa-docker', category: 'DevOps' },
    { name: 'NGINX', level: 70, icon: 'fa fa-server', category: 'DevOps' },
    { name: 'GIT', level: 80, icon: 'fab fa-git-alt', category: 'Tools' },
    { name: 'Postman', level: 70, icon: 'fa fa-paper-plane', category: 'Tools' },
    { name: 'PostgreSQL', level: 80, icon: 'fa fa-database', category: 'Database' },
    { name: 'MongoDB', level: 80, icon: 'fa fa-database', category: 'Database' }
];

// Reference to the about section element
const aboutSection = ref(null);
const hasAnimated = ref(false);

// Function to animate skill bars
const animateSkills = () => {
    if (hasAnimated.value) return; // Only animate once

    // Initialize all skills to 0
    skills.forEach(skill => {
        animatedSkills.value[skill.name] = 0;
    });

    // Trigger animation after a brief delay
    setTimeout(() => {
        skills.forEach(skill => {
            animatedSkills.value[skill.name] = skill.level;
        });
        hasAnimated.value = true;
    }, 100);
};

// Set up Intersection Observer to trigger animation when section is visible
onMounted(() => {
    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateSkills();
                }
            });
        },
        {
            threshold: 0.2 // Trigger when 20% of the section is visible
        }
    );

    if (aboutSection.value) {
        observer.observe(aboutSection.value);
    }

    // Cleanup observer on component unmount
    onUnmounted(() => {
        if (aboutSection.value) {
            observer.unobserve(aboutSection.value);
        }
    });
});

const certifications = [
    {
        name: "Software Engineering - Backend Specialist",
        issuer: "ALX Africa",
        date: "September 2024",
        link: "https://intranet.alxswe.com/certificates/2L8mznRG7s",
        id: "2L8mznRG7s",
        badge: "🎓"
    },
    {
        name: "Professional Developers(ProDev) - Frontend Program",
        issuer: "ALX Africa",
        date: "March 2025",
        link: "https://intranet.alxswe.com/certificates/23MxeNhFEX",
        id: "23MxeNhFEX",
        badge: "⚛️"
    },
    {
        name: "Artificial Intelligence Career Essentials",
        issuer: "ALX Africa",
        date: "November 2024",
        link: "https://intranet.alxswe.com/certificates/zhs7rEcpTZ",
        id: "zhs7rEcpTZ",
        badge: "🤖"
    },
    {
        name: "Backend Development Proficiency",
        issuer: "HNG Tech",
        date: "August 2024",
        link: "https://certgo.app/c-483e6427",
        id: "c-483e6427",
        badge: "⚙️"
    },
    {
        name: "DevOps Engineering Proficiency",
        issuer: "HNG Tech",
        date: "August 2024",
        link: "https://certgo.app/c-56928c41",
        id: "c-56928c41",
        badge: "☁️"
    },
    {
        name: "Mobile Development Proficiency",
        issuer: "HNG Tech",
        date: "August 2024",
        link: "https://certgo.app/c-d34b3ece",
        id: "c-d34b3ece",
        badge: "📱"
    }
];
</script>
