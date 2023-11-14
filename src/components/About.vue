<script></script>

<template>
    <section class="about">
        <picture class="about-img-dark">
            <source media="(max-width: 768px)" srcset="../assets/images/mobile-image-about-dark.jpg">
            <img src="../assets/images/image-about-dark.jpg" alt="image-about-dark">
        </picture>
        <article class="about-info">
            <h2 class="about-info-title">ABOUT OUR FURNITURE</h2>
            <p class="about-info-text">
                Our multifunctional collection blends design and function to suit your individual taste.
                Make each room unique, or pick a cohesive theme that best express your interests and what
                inspires you. Find the furniture pieces you need, from traditional to contemporary styles
                or anything in between. Product specialists are available to help you create your dream space.
            </p>
        </article>
        <picture class="about-img-light">
            <source media="(max-width: 768px)" srcset="../assets/images/mobile-image-about-light.jpg">
            <img src="../assets/images/image-about-light.jpg" alt="image-about-dark">
        </picture>
    </section>
</template>

<style scoped>
.about {
    width: 100%;
    height: 266px;
    display: flex;
}
.about-img-dark {
    width: 100%;
    max-width: 420px;
}
.about-info {
    width: 100%;
    max-width: 580px;
    padding: 4.1rem 3rem 0;
}
.about-info-title {
    font-size: 1rem;
    letter-spacing: .42rem;
}
.about-info-text {
    margin-top: .85rem;
    font-weight: 300;
    line-height: 1.37rem;
    letter-spacing: .002rem;
    color: var(--dark-gray);
}
.about-img-light {
    width: 100%;
    max-width: 440px;
}

.about-img-dark img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

/* Media Query */
@media screen and (max-width: 1280px) {
    .about-info {
        padding: 2.5rem 2rem 0;
    }
}

@media screen and (max-width: 1180px) {
    .about-info {
        min-width: 400px;
        padding: 2rem;
    }
    .about-img-light img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
}

@media screen and (max-width: 768px) {
    .about {
        height: fit-content;
        flex-direction: column;
    }
    .about-img-dark,
    .about-img-light {
        max-width: none;
    }
    .about-info {
        max-width: none;
        padding: 4rem 2rem;
    }
    .about-info-text {
        margin-top: 2rem;
    }
}

@media screen and (max-width: 520px) {
    .about-info-title {
        font-size: .9rem;
        letter-spacing: .34rem;
    }

    .about-info {
        min-width: 0;
        padding: 2rem;
    }
}
</style>