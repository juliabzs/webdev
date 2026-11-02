<script setup>
import { Mail, Phone, Linkedin, MapPin } from 'lucide-vue-next';
import { reactive, ref } from 'vue';

const contactInfo = [
    {
        id: 1,
        icon: Mail,
        title: 'Email',
        value: 'jubabzds@gmail.com',
        link: 'mailto:hello@example.com'
    },
    {
        id: 2,
        icon: Phone,
        title: 'Phone',
        value: '+55 (11) 96593-5200',
        link: 'tel:+5511912345678'
    },
    {
        id: 3,
        icon: Linkedin,
        title: 'LinkdIn',
        value: 'https://www.linkedin.com/in/julia-bezerra-861146380/',
        link: '#'
    },
    {
        id: 4,
        icon: MapPin,
        title: 'Location',
        value: 'São Paulo, BR',
        link: null
    }
]
const formData = reactive({
    email: '',
    subject: '',
    message: ''
})

const isSubmitting = ref (false)

const handleSubmit = async () => {
    isSubmitting.value = true

    try {
        formData.email = ''
        formData.subject = ''
        formData.message = ''
    } catch (error) {
        alert('Falha ao enviar mensagem. Por favor, tente novamente.')
    } finally {
        isSubmitting.value = false
    }
}

</script>

<template>
    <section class="py-20 bg-gray-900" id="contact">
        <div class="container mx-auto px-4 max-w-6xl">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-5xl font-extrabold
            text-white mb-2">
                    Let's Connect.
                </h2>
                <div class="w-28 h-1 bg-primary mx-auto mt-2
            rounded-2xl"></div>
            </div>
            <div class="grid md:grid-cols-2 gap-8">
                <div>
                    <p class="text-gray-400 mb-8 leading-relaxed">
                        Tens um projeto em mente ou precisas de ajuda para tirar uma ideia do papel? 
                        Envia-me uma mensagem ou entra em contato direto através dos canais abaixo. 
                    </p>
                    <div class="space-y-6">
                        <div
                        v-for="info in contactInfo"
                        :key="info.id"
                        class="flex items-center gap-4 group">
                        <div class="w-10 h-10 rounded-full bg-primary/10
                flex items-center justify-center group-hover:bg-primary/20
                transition-colors">
                                <component :is="info.icon" :size="18" class="text-primary"/>
                            </div>
                            <div>
                                <h4 class="text-white font-medium text-sm">
                                    {{ info.title }}
                                </h4>
                                <a
                                v-if="info.link"
                                :href="info.link"
                                class="text-gray-400 text-sm
                        hover:text-primary transition-colors"
                                :target="info.title === 'Location'
                                ? '_self'
                                : '_blank'"
                                :ref="info.title === 'Location' ? ''
                                : 'noopener noreferrer'">
                                   {{ info.value }}  
                                </a>
                                <p v-else class="text-gray-400 text-sm">
                                    {{ info.value }}
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
                <!--Form-->
                <div class="bg-gray-800 rounded-lg p-6">
                    <form @submit.prevent="handleSubmit">
                        <!--E-mail-->
                        <div class="mb-4">
                            <label for="email"
                            class="text-white block mb-2 text-sm
                            font-medium">
                                Email
                            </label>
                            <input
                            type="email" id="email"
                            v-model="formData.email"
                            class="w-full px-4 py-2 bg-gray-700
                            border-gray-600 rounded-lg
                            text-white text-sm focus:outline-none
                            focus:border-primary transition-colors"
                            placeholder="seu@email.com"
                            required>
                        </div>
                        <!--Message-->
                        <div class="mb-6">
                            <label for="message"
                            class="text-white block mb-2 text-sm
                            font-medium">
                                Message
                            </label>
                            <textarea
                            id="message"
                            v-model="formData.message"
                            class="w-full px-4 py-2 bg-gray-700
                            border-gray-600 rounded-lg
                            text-white text-sm focus:outline-none
                            focus:border-primary transition-colors"
                            placeholder="Me fale sobre seu Projeto"
                            rows="4"
                            required />
                        </div>
                        <button
                        type="submit"
                        :disabled="isSubmitting"
                        class="w-full px-6 py-2.5 bg-primary text-white
                        rounded-lg font-medium hover:bg/primary/80
                        transition-colors disabled:opacity-50
                        disabled:cursor-not-allowed">
                        {{ isSubmitting ? 'Sending...' : 'Send Message' }}
                        </button>
                    </form>

                </div>
            </div>
        </div>
    </section>
</template>