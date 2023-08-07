<template>
    <div class="mx-auto max-w-screen min-h-screen bg-black text-white md:px-10 px-3">
        <div class="fixed top-[-50px] hidden lg:block">
            <img src="/images/signup-image.png" class="hidden laptopLg:block laptopLg:max-w-[450px] laptopXl:max-w-[640px]"
                alt="">
        </div>

        <div class="py-24 flex laptopLg:ml-[680px] laptopXl:ml-[870px]">
            <div>
                <img src="/images/moonton-white.svg" alt="">
                <div class="my-[70px]">
                    <div class="font-semibold text-[26px] mb-3">
                        Sign Up
                    </div>
                    <p class="text-base text-[#767676] leading-7">
                        Explore our new movies and get <br>
                        the better insight for your life
                    </p>
                </div>
                <form class="w-[370px]">
                    <div class="flex flex-col gap-6">
                        <div>
                            <InputLabel for="fullname" value="Full Name" />

                            <TextInput id="fullname" type="text" name="fullname" v-model="form.fullname" required
                                autocomplete="off" placeholder="Your Full Name..." value="Raden Andhika" />
                        </div>
                        <div>
                            <InputLabel for="email" value="Email Address" />

                            <TextInput id="email" type="email" name="email" v-model="form.fullname" required
                                autocomplete="off" placeholder="Your Email Address..." value="rantara@gmail.com" />
                        </div>
                        <div>
                            <InputLabel for="password" value="Password" />

                            <TextInput id="password" type="password" name="password" v-model="form.fullname" required
                                autocomplete="off" placeholder="Input Password" value="Dika0501" />
                        </div>
                    </div>
                    <div class="grid space-y-[14px] mt-[30px]">
                        <PrimaryButton :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Sign Up
                        </PrimaryButton>

                        <SecondaryButton>
                            <Link href="signin" preserve-scroll>SignIn to My Account</Link>
                        </SecondaryButton>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script setup>
import TextInput from '@/Components/TextInput.vue'
import PrimaryButton from '@/Components/PrimaryButton.vue'
import SecondaryButton from '@/Components/SecondaryButton.vue'
import InputLabel from '@/Components/InputLabel.vue'
import { Head, Link, useForm } from '@inertiajs/vue3'

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    fullname: '',
    email: '',
    password: '',
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>