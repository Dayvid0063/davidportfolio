<!-- pages/index.vue -->
<template>
    <div class="min-h-screen bg-navy-900 text-slate-200 selection:bg-emerald-500/30 selection:text-emerald-200">
        <Header />
        <main>
            <HeroSection />
            <AboutSection />
            <ProjectsSection />
            <ContactSection />
        </main>
        <Footer />
    </div>
</template>

<script setup>
useHead({
    title: 'David Orji | Software Engineer',
    meta: [
        { name: 'description', content: 'Software Engineer Portfolio showcasing projects and skills' }
    ]
});
</script>

<style>
html {
    scroll-behavior: smooth;
    overflow-x: hidden;
}

body {
    font-family: 'DM Sans', sans-serif;
    overflow-x: hidden;
}

* {
    box-sizing: border-box;
}
</style>
