<!-- components/ContactSection.vue -->
<template>
    <section id="contact" class="py-20 bg-navy-900 relative overflow-hidden">
        <div class="absolute top-1/2 left-0 w-64 h-64 bg-teal-600/10 rounded-full blur-[80px] -translate-y-1/2"></div>
        <div class="absolute bottom-0 right-0 w-96 h-96 bg-emerald-600/10 rounded-full blur-[100px]"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
                <!-- Left Column - Contact Info -->
                <div class="space-y-6">
                    <div>
                        <h2 class="text-3xl md:text-4xl font-bold text-white mb-3">{{ $t('contact.title') }}</h2>
                        <p class="text-slate-400">
                            {{ $t('contact.subtitle') }}
                        </p>
                    </div>

                    <div class="space-y-4">
                        <div
                            class="bg-navy-800/50 backdrop-blur-md border border-white/10 rounded-xl p-5 flex items-start space-x-4">
                            <div class="p-2.5 bg-emerald-500/10 rounded-lg">
                                <i class="fa fa-envelope text-emerald-400 text-lg"></i>
                            </div>
                            <div>
                                <h3 class="text-base font-semibold text-white">{{ $t('contact.email') }}</h3>
                                <p class="text-slate-400 text-sm">orjidavid0063@gmail.com</p>
                            </div>
                        </div>

                        <!-- <div
                            class="bg-navy-800/50 backdrop-blur-md border border-white/10 rounded-xl p-5 flex items-start space-x-4">
                            <div class="p-2.5 bg-blue-500/10 rounded-lg">
                                <i class="fa fa-phone text-blue-400 text-lg"></i>
                            </div>
                            <div>
                                <h3 class="text-base font-semibold text-white">{{ $t('contact.phone') }}</h3>
                                <p class="text-slate-400 text-sm">+234 XXX XXX XXXX</p>
                            </div>
                        </div> -->

                        <div
                            class="bg-navy-800/50 backdrop-blur-md border border-white/10 rounded-xl p-5 flex items-start space-x-4">
                            <div class="p-2.5 bg-teal-500/10 rounded-lg">
                                <i class="fa fa-map-marker-alt text-teal-400 text-lg"></i>
                            </div>
                            <div>
                                <h3 class="text-base font-semibold text-white">{{ $t('contact.location') }}</h3>
                                <p class="text-slate-400 text-sm">Lagos, Nigeria</p>
                            </div>
                        </div>
                    </div>

                    <div
                        class="p-5 bg-gradient-to-r from-emerald-900/20 to-teal-900/20 rounded-2xl border border-white/5">
                        <h3 class="text-white font-semibold mb-2 text-sm">{{ $t('contact.currentStatus') }}</h3>
                        <div class="flex items-center space-x-2">
                            <span class="relative flex h-3 w-3">
                                <span
                                    class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"></span>
                                <span class="relative inline-flex rounded-full h-3 w-3 bg-green-500"></span>
                            </span>
                            <span class="text-green-400 font-medium text-sm">{{ $t('contact.available') }}</span>
                        </div>
                    </div>
                </div>

                <!-- Right Column - Contact Form -->
                <div class="bg-navy-800/50 backdrop-blur-md border border-white/10 rounded-xl p-6">
                    <!-- Success Message -->
                    <div v-if="isSubmitted" class="text-center py-8">
                        <div
                            class="w-16 h-16 bg-gradient-to-r from-green-500 to-emerald-500 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fa fa-check text-white text-2xl"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-2">{{ $t('contact.form.successTitle') }}</h3>
                        <p class="text-slate-400 mb-6">
                            {{ $t('contact.form.successMessage') }}
                        </p>
                        <button @click="resetForm"
                            class="px-6 py-2.5 bg-gradient-to-r from-emerald-500 to-teal-500 text-white rounded-lg font-semibold hover:from-emerald-600 hover:to-teal-600 transition-all duration-300">
                            {{ $t('contact.form.sendAnother') }}
                        </button>
                    </div>

                    <!-- Form -->
                    <form v-else @submit.prevent="handleSubmit" class="space-y-5">
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
                            <div class="w-full">
                                <label for="name" class="block text-sm font-medium text-slate-300 mb-1.5">{{
                                    $t('contact.form.name') }}</label>
                                <input id="name" v-model="formData.name"
                                    class="w-full px-4 py-2.5 bg-navy-900/50 border border-slate-700 rounded-lg text-white placeholder-slate-500 focus:outline-none focus:ring-2 focus:ring-emerald-500/50 focus:border-emerald-500 transition-colors duration-200"
                                    :placeholder="$t('contact.form.namePlaceholder')" required />
                            </div>
                            <div class="w-full">
                                <label for="email" class="block text-sm font-medium text-slate-300 mb-1.5">{{
                                    $t('contact.form.email') }}</label>
                                <input id="email" v-model="formData.email" type="email"
                                    class="w-full px-4 py-2.5 bg-navy-900/50 border border-slate-700 rounded-lg text-white placeholder-slate-500 focus:outline-none focus:ring-2 focus:ring-emerald-500/50 focus:border-emerald-500 transition-colors duration-200"
                                    :placeholder="$t('contact.form.emailPlaceholder')" required />
                            </div>
                        </div>

                        <div class="w-full">
                            <label for="subject" class="block text-sm font-medium text-slate-300 mb-1.5">{{
                                $t('contact.form.subject') }}</label>
                            <input id="subject" v-model="formData.subject"
                                class="w-full px-4 py-2.5 bg-navy-900/50 border border-slate-700 rounded-lg text-white placeholder-slate-500 focus:outline-none focus:ring-2 focus:ring-emerald-500/50 focus:border-emerald-500 transition-colors duration-200"
                                :placeholder="$t('contact.form.subjectPlaceholder')" required />
                        </div>

                        <div class="w-full">
                            <label for="message" class="block text-sm font-medium text-slate-300 mb-1.5">{{
                                $t('contact.form.message') }}</label>
                            <textarea id="message" v-model="formData.message"
                                class="w-full px-4 py-2.5 bg-navy-900/50 border border-slate-700 rounded-lg text-white placeholder-slate-500 focus:outline-none focus:ring-2 focus:ring-emerald-500/50 focus:border-emerald-500 transition-colors duration-200 min-h-[100px] resize-y"
                                :placeholder="$t('contact.form.messagePlaceholder')" required></textarea>
                        </div>

                        <!-- Error Message -->
                        <div v-if="errorMessage"
                            class="text-center text-red-400 bg-red-900/20 p-3 rounded-lg border border-red-500/30">
                            <i class="fa fa-exclamation-circle mr-2"></i>
                            {{ errorMessage }}
                        </div>

                        <button type="submit" :disabled="isSubmitting" :class="[
                            'inline-flex items-center justify-center rounded-lg font-medium transition-all duration-200 px-8 py-3 text-base w-full',
                            isSubmitting
                                ? 'bg-slate-600 text-slate-300 cursor-not-allowed opacity-70'
                                : 'bg-emerald-500 text-white hover:bg-emerald-600 shadow-lg shadow-emerald-500/25'
                        ]">
                            <template v-if="isSubmitting">
                                <i class="fa fa-spinner fa-spin mr-2"></i>
                                {{ $t('contact.form.sending') }}
                            </template>
                            <template v-else>
                                {{ $t('contact.form.submit') }}
                                <i class="fa fa-paper-plane ml-2"></i>
                            </template>
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
const config = useRuntimeConfig();
const formspreeKey = config.public.formspreeKey;

const formData = ref({
    name: '',
    email: '',
    subject: '',
    message: ''
});

const isSubmitting = ref(false);
const isSubmitted = ref(false);
const errorMessage = ref('');

const handleSubmit = async () => {
    isSubmitting.value = true;
    errorMessage.value = '';

    try {
        const response = await $fetch(`https://formspree.io/f/${formspreeKey}`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(formData.value)
        });

        isSubmitted.value = true;
    } catch (error) {
        console.error('Form submission error:', error);
        errorMessage.value = $t('contact.form.error');
    } finally {
        isSubmitting.value = false;
    }
};

const resetForm = () => {
    formData.value = {
        name: '',
        email: '',
        subject: '',
        message: ''
    };
    isSubmitted.value = false;
    errorMessage.value = '';
};
</script>
