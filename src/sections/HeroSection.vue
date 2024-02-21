<script setup>
import { ref } from "vue";
import Swal from "sweetalert2";

let email = ref("");
let emailError = ref(false);
const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

let handleSubmit = () => {
    if (!email.value || !emailRegex.test(email.value)) {
        emailError.value = true;
    } else {
        console.log(emailRegex.test(email.value));
        Swal.fire({
            icon: "success",
            title: "Thank You",
            text: `${email.value} subscribed to our newsletter!`,
        });
    }
};
</script>

<template>
    <!-- Hero Section Start -->
    <div class="container mx-auto px-5 overflow-x-hidden lg:overflow-x-visible">
        <section class="grid grid-cols-none lg:grid-cols-2 pb-16 pt-8 items-center">
            <div class="lg:w-5/6 order-2 lg:order-none">
                <h1 class="text-4xl xl:text-5xl font-bold font-theme-heading text-center lg:text-left"> Augmenting Sales for DMV SMBs With Fine-Tuned Transformative GenAI</h1>
                <p class="text-theme-grayish-blue text-left mt-7 font-theme-content text-2xl">Harnessing the power of custom-trained Large Language Models (LLMs) to redefine sales for businesses across the DC, Maryland and Virginia region. Our suite of tools are fine-tuned on DMV consumer data, designed to elevate your lead generation and deal-closing capabilities to unprecedented heights.</p>
                <div class="flex justify-center lg:justify-start mt-10">
                    <form @submit.prevent="handleSubmit()">
                    <div class="relative flex flex-col items-center lg:flex-row justify-center lg:space-x-3">
                        <div class="relative w-full lg:mb-0 font-theme-content">
                            <input v-model="email" @input="emailError = false" class="w-full py-3 px-5 text-sm text-gray-600 border-0 shadow-md rounded focus:ring-4 focus:ring-blue-300" type="text" name="newsletter_email" placeholder="Enter your email address" />
                            <div v-show="emailError">
                                <img class="absolute right-3 top-3" src="/images/icon-error.svg" alt="Error Icon" />
                                <div class="absolute w-full text-xs italic px-2 py-1 bg-theme-secondary text-white rounded">Whoops, make sure it's an email</div>
                            </div>
                        </div>

                        <Button type="submit" btn-type="secondary" class="whitespace-nowrap">Learn More</Button>
                    </div>
                </form>
                </div>
            </div>
            <div class="relative order-1 lg:order-none mb-20 lg:mt-0 lg:mb-0 lg:-mr-10">
                <img class="z-10 w-full" src="/images/illustration-hero.svg" />
                <div class="-z-10 bg-theme-primary h-52 w-full sm:h-80 sm:w-full rounded-l-full absolute -right-28 md:-right-48 -bottom-8"></div>
            </div>
        </section>
    </div>
    <!-- Hero Section End -->
</template>
