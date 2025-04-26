<script setup>
import { defineAsyncComponent } from 'vue'
import Logo from '@/assets/Logo.png'

const UserForm = defineAsyncComponent(() => import('./components/UserForm.vue'))
const AdditionalDetails = defineAsyncComponent(() => import('./components/AdditionalDetails.vue'))
</script>

<template>
    <div class="full-page-wrapper">
        <div class="app-wrapper">
            <header class="app-header" role="banner">
                <!-- Header Content -->
                <img :src="Logo" alt="Company Logo" class="header-logo" loading="eager" fetchpriority="high" />
            </header>
            <section class="app-content" aria-labelledby="app-content-section">
                <UserForm />
                <AdditionalDetails />
            </section>
        </div>
    </div>
</template>

<style scoped>
.full-page-wrapper {
    height: 100vh;
    width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0;
    padding: 0;
    background-color: #ECF8FB;
    animation: background-color-transition 10s infinite alternate;
}

@keyframes background-color-transition {
    0% {
        background-color: #ECF8FB;
    }
    100% {
        background-color: #EFEFEF;
    }
}

/* App layout */
.app-wrapper {
    width: 60%;
    min-width: 1024px;
    height: 100vh;
    display: flex;
    flex-direction: column;
    overflow: hidden;
}

.app-header {
    height: 80px;
    background-color: #545253;
    flex-shrink: 0;
    display: flex;
    justify-content: center;
    align-items: center;
}

.app-content {
    flex: 1;
    width: 100%;
    background-color: rgba(255, 255, 255, 0.5);
    background-blend-mode: overlay;
    padding: 24px;
    box-sizing: border-box;
    overflow-y: auto;
    scrollbar-width: none;
    -ms-overflow-style: none;
    background-image: url('@/assets/background.svg');
    background-repeat: repeat-x;
    background-size: auto 101%;
    background-position: top left;
    background-attachment: fixed;
}

.app-content::-webkit-scrollbar {
    width: 0px;
}

.app-content:hover::-webkit-scrollbar {
    width: 6px;
}

.app-content::-webkit-scrollbar-track {
    background: transparent;
}

.app-content::-webkit-scrollbar-thumb {
    background-color: rgba(0, 0, 0, 0.4);
    border-radius: 3px;
}

.header-logo {
    max-height: 60px;
    max-width: 100%;
}

@media (max-width: 767px) {
    .full-page-wrapper {
        background-image: url('@/assets/background.svg');
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        background-color: #ECF8FB;
        background-attachment: scroll;
        overflow: hidden;
    }

    .app-wrapper {
        width: 100%;
        min-width: 0;
        height: 100vh;
        display: flex;
        flex-direction: column;
    }

    .app-header {
        height: 60px;
    }

    .header-logo {
        max-height: 50px;
    }

    .app-content {
        flex: 1;
        width: 100%;
    }
}
</style>
