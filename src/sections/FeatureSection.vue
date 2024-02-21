<script setup>

import features from '../data/features.js';
import { ref } from 'vue';

let isOpen = ref(1);

</script>

<template>
    <!-- Features Section Start -->
    <div id="features" class="container mx-auto px-5">
        <section class="py-16">
            <div class="w-4/5 md:w-3/5 mx-auto">
                <h2 class="text-3xl md:text-4xl font-semibold font-theme-heading text-center">LLM-Powered Tools That Boost DMV Enterprise</h2>
                <p class="text-theme-grayish-blue text-left mt-7 font-theme-content text-2xl">Our tools come in either Standard, Synthetic or Custom versions. Standard version uses data you provide to fine-tune the service as is, with no manipulation of the data whasoever before input. Synthetic version uses either Generative Adversarial Networks (GANs) or Variational Autoencoders (VAEs) techniques on a case-by-case basis to replace your input data with synthetic versions that match in statistical properties while ensuring privacy and confidentiality of the input data. Custom version also uses synthetic data but creates a custom model for your business as well, fine-tuned to your needs and able to be ran locally. Please sign up and contact us to discuss pricing. </p>
            </div>

            <div class="mt-10">
                <ul class="flex flex-col items-center md:flex-row justify-center font-theme-heading">
                    <li v-for="feature in features" :key="feature.id" :class="isOpen === feature.id ? 'md:border-b-4 md:border-theme-secondary' : ''" class="w-full md:w-56 cursor-pointer hover:text-theme-secondary transition duration-200 border-b-2 border-t-2 md:border-t-0 flex justify-center">
                        <a @click.prevent="isOpen = feature.id" href="#" :class="isOpen === feature.id ? ' border-theme-secondary' : ''" class="py-5  md:border-b-0 border-b-4">{{ feature.name }}</a>
                    </li>
                </ul>
            </div>

            <div class="mt-16">
                <!-- Tab Content -->
                <template v-for="feature in features" :key="feature.id">
                    <div v-show="isOpen === feature.id" class="grid gap-32 lg:grid-cols-2 items-center">
                        <div class="relative">
                            <img class="z-10 w-full" :src="feature.details.imageUrl" />
                            <div class="-z-10 bg-theme-primary h-52 w-96 sm:h-80 sm:w-full rounded-r-full absolute -left-56 -bottom-16"></div>
                        </div>
                        <div>
                            <h3 class="font-theme-heading text-4xl md:text-3xl font-medium text-center lg:text-left">{{ feature.details.title }}</h3>
                            <p class="mt-7 font-theme-content text-2xl text-theme-grayish-blue text-center lg:text-left">{{ feature.details.description }}</p>
                            
                        </div>
                    </div>
                </template>
                <!-- Tab Content -->
            </div>
        </section>
    </div>
    <!-- Features Section End -->
</template>
