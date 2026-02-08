<!-- components/FloatingParticles.vue -->
<template>
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
        <div v-for="(particle, index) in particles" :key="index" class="absolute" :style="{
            left: particle.x + '%',
            top: particle.y + '%',
        }">
            <div class="rounded-full" :style="{
                width: particle.size + 'px',
                height: particle.size + 'px',
                background: `radial-gradient(circle, ${particle.color} 0%, transparent 70%)`,
                opacity: particle.opacity,
                animation: `float-${index} ${particle.duration}s ease-in-out infinite`,
                animationDelay: particle.delay + 's',
                filter: 'blur(1px)'
            }"></div>
        </div>
    </div>
</template>

<script setup>
const particles = ref([]);

onMounted(() => {
    const colors = [
        'rgba(16, 185, 129, 0.8)',   // emerald-500
        'rgba(20, 184, 166, 0.8)',   // teal-500
        'rgba(52, 211, 153, 0.7)',   // emerald-400
        'rgba(45, 212, 191, 0.7)',   // teal-400
        'rgba(110, 231, 183, 0.6)',  // emerald-300
    ];

    const particleCount = 50;

    particles.value = Array.from({ length: particleCount }, (_, i) => {
        const size = Math.random() * 6 + 2; // 2-8px (increased from 1-5px)
        return {
            id: i,
            size,
            x: Math.random() * 100,
            y: Math.random() * 100,
            color: colors[Math.floor(Math.random() * colors.length)],
            duration: Math.random() * 20 + 10, // 10-30s
            delay: Math.random() * 5,
            opacity: Math.random() * 0.4 + 0.5, // 0.5-0.9 (increased from 0.3-0.8)
            translateX: (Math.random() - 0.5) * 100,
            translateY: (Math.random() - 0.5) * 100,
        };
    });

    // Inject dynamic keyframes
    const styleSheet = document.createElement('style');
    styleSheet.type = 'text/css';
    let keyframesString = '';

    particles.value.forEach((particle, index) => {
        keyframesString += `
      @keyframes float-${index} {
        0%, 100% {
          transform: translate(0, 0);
        }
        25% {
          transform: translate(${particle.translateX * 0.5}px, ${particle.translateY * 0.5}px);
        }
        50% {
          transform: translate(${particle.translateX}px, ${particle.translateY}px);
        }
        75% {
          transform: translate(${particle.translateX * 0.5}px, ${-particle.translateY * 0.5}px);
        }
      }
    `;
    });

    styleSheet.innerHTML = keyframesString;
    document.head.appendChild(styleSheet);
});
</script>
