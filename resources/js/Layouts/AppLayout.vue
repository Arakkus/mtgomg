<template>
    <div class="layout">
        <Head :title="title" />

        <jet-banner />

        <div class="flex">
            <Navigation/>
            <div class="content">
                <!-- Page Heading -->
                <header class="bg-white shadow" v-if="$slots.header">
                    <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                        <slot name="header"></slot>
                    </div>
                </header>

                <!-- Page Content -->
                <main>
                    <slot></slot>
                </main>
            </div>
        </div>
    </div>
</template>

<script>
    import JetBanner from '@/Jetstream/Banner.vue'
    import { Head } from '@inertiajs/inertia-vue3';
    import Navigation from '@/Components/Navigation.vue';

    export default {
        props: {
            title: String,
        },

        components: {
            Head,
            JetBanner,
            Navigation,
        },
    }
</script>
