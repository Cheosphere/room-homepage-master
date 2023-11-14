<script setup>
import { ref } from 'vue'

const iconHamburger = ref(null)
const navMenu = ref(null)

const menuMobile = () => {
    navMenu.value.classList.toggle('show-menu')
    iconHamburger.value.classList.toggle('change-icon')
}

</script>

<template>
    <header class="header">
        <figure class="header-logo">
            <img src="../assets/images/logo.svg" alt="logo image">
        </figure>
        <nav class="nav" ref="navMenu">
            <ul class="nav-menu">
                <li class="nav-menu-item"><a href="javascript:;">home</a></li>
                <li class="nav-menu-item"><a href="javascript:;">shop</a></li>
                <li class="nav-menu-item"><a href="javascript:;">about</a></li>
                <li class="nav-menu-item"><a href="javascript:;">contact</a></li>
            </ul>
        </nav>
        <span class="icon-hamburger" ref="iconHamburger" @click="menuMobile"></span>
    </header>
</template>

<style scoped>
.header {
    padding: 4rem;
    display: flex;
    position: absolute;
}
.icon-hamburger {
    width: 20px;
    height: 14px;
    display: none;
    background-image: url('../assets/images/icon-hamburger.svg');
    background-repeat: no-repeat;
    background-position: center;
    cursor: pointer;
    transition: .5s ease-out;
}
.nav {
    margin-left: 3.55rem;
}
.nav-menu {
    display: flex;
    
}
.nav-menu-item {
    margin-top: -.2rem;
    margin-right: 2rem;
    list-style: none;
}

a {
    color: var(--white);
    text-decoration: none;
    letter-spacing: -.02rem;
}

/* Media Query */
@media screen and (max-width: 1180px) {
    .header {
        left: 0;
    }
}

@media screen and (max-width: 768px) {
    .nav {
        width: 100%;
        height: 100%;
        margin-left: 0;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        position: absolute;
        top: -12rem;
        left: 0;
        background-color: var(--white);
        transition: .3s ease-in-out;
    }
    .header {
        width: 100%;
        justify-content: center;
        flex-direction: row-reverse;
    }
    .header-logo {
        margin-right: auto;
    }

    a {
        color: var(--black);
    }
    .icon-hamburger {
        display: block;
        margin-right: auto;
        z-index: 10;
    }
    .show-menu {
        top: 0;
    }
    .change-icon {
        background-image: url('../assets/images/icon-close.svg');
        background-position: center;
        transform: rotate3d(0, 1, 0, 180deg);
    }
}

@media screen and (max-width: 580px) {
    .header {
        padding: 3rem 2rem;
    }
}

@media screen and (max-width: 374px) {
    .header {
        padding: 3rem 1rem;
    }
    .nav-menu-item {
        margin-right: 1.5rem;
    }
}
</style>