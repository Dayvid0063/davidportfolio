<!-- components/ProjectCard.vue -->
<template>
    <div
        class="bg-navy-800/50 backdrop-blur-md border border-white/10 rounded-xl overflow-hidden transition-all duration-300 hover:-translate-y-1 hover:shadow-xl hover:shadow-emerald-500/10 hover:border-emerald-500/30 flex flex-col h-full group">
        <div class="relative overflow-hidden aspect-video">
            <NuxtImg :src="project.image" :alt="project.title"
                class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" />
            <div
                class="absolute inset-0 bg-navy-900/80 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center gap-4 backdrop-blur-sm">
                <a :href="project.github"
                    class="p-3 bg-white/10 rounded-full text-white hover:bg-emerald-500 hover:scale-110 transition-all duration-200"
                    title="View Code">
                    <i class="fab fa-github text-xl"></i>
                </a>
                <a :href="project.demo"
                    class="p-3 bg-white/10 rounded-full text-white hover:bg-emerald-500 hover:scale-110 transition-all duration-200"
                    title="View Demo">
                    <i class="fa fa-external-link-alt text-xl"></i>
                </a>
            </div>
        </div>

        <div class="p-6 flex-1 flex flex-col">
            <h3 class="text-xl font-bold text-white mb-2 group-hover:text-emerald-400 transition-colors">
                {{ project.title }}
            </h3>
            <p class="text-slate-400 text-sm mb-4 flex-1">
                {{ project.description }}
            </p>
            <div class="flex flex-wrap gap-2 mt-auto">
                <span v-for="tech in project.technologies" :key="tech"
                    class="px-2 py-1 text-xs font-medium text-emerald-300 bg-emerald-900/30 rounded border border-emerald-500/20">
                    {{ tech }}
                </span>
            </div>
        </div>
    </div>
</template>

<script setup>
defineProps({
    project: {
        type: Object,
        required: true
    }
});
</script>
