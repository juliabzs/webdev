<script setup>
import { Award, ExternalLink, ShieldCheck } from 'lucide-vue-next';

const certifications = [
    {
        id: 1,
        title: 'Introdução à computação: ambientes e ferramentas de programação',
        issuer: 'Alura',
        date: 'Abril 2024',
        link: "https://drive.google.com/file/d/1WRFe5JfXHD-1ZkCcrLq-4PQVHaPPDDQu/view?usp=sharing",
        desc: ''
    },
    {
        id: 2,
        title: 'Modelagem de Banco de Dados Relacional: Entendendo SQL',
        issuer: 'Alura',
        date: 'Maio 2024',
        link: "https://drive.google.com/file/d/1q80qyhFM6f3hTfaBkljYnJvaxIXct21B/view?usp=sharing",
        desc: ''
    },
    {
        id: 3,
        title: 'Linguagem de Programação: Criando Projetos Artísticos com JAVASCRIPT',
        issuer: 'Alura',
        date: 'Maio 2024',
        link: "https://drive.google.com/file/d/1VSxMLuqguM9tSkpkJyObxuOjHioqJaB9/view?usp=sharing",
        desc: ''
    },
    {
        id: 4,
        title: 'JAVASCRIPT: Manipulando o Dom',
        issuer: 'Alura',
        date: 'Maio 2024',
        link: "https://drive.google.com/file/d/1cgkZMEUcb-Ic9K3ZyT2ZhW98-8BTDGxs/view?usp=sharing",
        desc: ''
    },
    {
        id: 5,
        title: 'MongoDB: conhecendo um banco de dados NoSQL',
        issuer: 'Alura',
        date: 'May 2024',
        link: "https://drive.google.com/file/d/1UFiEvGL6WlCbAw-f8dWOv0pNV1vcty4M/view?usp=sharing",
        desc: ''
    },
    {
        id: 6,
        title: 'Modelagem de banco de dados relacional: entenendo o SQL',
        issuer: 'Alura',
        date: 'Dec 2023',
        link: "https://drive.google.com/file/d/1HCi_0sJYDhElxwFlbFrV1zghl_wzvO1W/view?usp=sharing",
        desc: ''
    }
]

</script>

<template>
    <section class="text-white py-20" id="certificates">
        <div class="max-w-7xl mx-auto px-6 lg:px-16">
            <div class="mb-16">
                <p class="text-primary text-sm uppercase mb-2
                tracking-widest font-semibold">
                    Achievements
                </p>
                <h2 class="text-4xl md:text-5xl font-extrabold
                text-white">
                Certifications.
                </h2>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3
            gap-6">
            <div
            v-for="cert in certifications"
            :key="cert.id"
            data-aos="zoom-in"
            class="group relative bg-[#111a3e] border
            border-[#1f1641] p-6 rounded-2xl transition-all
            duration-300 hover:border-primary/50
            hover:shadow-[0_0_20px_-5px_rgba(6, 162, 194, 0.2)]">
            <div class="absolute -top-4 -right-4 bg-primary
            p-3 rounded-xl shadow-lg transform
            group-hover:rotate-12 transition-transform">
                <Award class="text-white" :size="24"/>
            </div>
            <div class="flex items-center gap-4 mb-4 text-xs
            text-gray-400">
            <span class="flex items-center gap-1">
                <ShieldCheck :size="14" class="text-primary"/>
                {{ cert.issuer }}
            </span>
            </div>
            <h3 class="text-xl font-bold mb-3
            group-hover:text-primary transition-colors">
                {{ cert.title }}
            </h3>
            <p class="text-gray-400 text-sm mb-6 line-clamp-2">
                {{ cert.desc }}
            </p>
            <a :href="cert.link"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-2 text-sm
            font-medium text-primary hover:text-white
            transition-colors border-b border-transparent
            hover:border-white pb-1">
            View Certificate <ExternalLink :size="14"/>
            </a>
        </div>
        </div>
        </div>

    </section>
</template>