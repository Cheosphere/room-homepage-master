<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const heroContent = [
    {
        title: 'Discover innovative ways to decorate',
        content: 'We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.',
        desktop_img: 'src/assets/images/desktop-image-hero-1.jpg',
        mobile_img: 'src/assets/images/mobile-image-hero-1.jpg'
    },
    {
        title: 'We are available all across the globe',
        content: "With stores all over the world, it's easy for you to find furniture for your home or place of business. Locally, we’re in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don't hesitate to contact us today.",
        desktop_img: 'src/assets/images/desktop-image-hero-2.jpg',
        mobile_img: 'src/assets/images/mobile-image-hero-2.jpg'
    },
    {
        title: 'Manufactured with the best materials',
        content: 'Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.',
        desktop_img: 'src/assets/images/desktop-image-hero-3.jpg',
        mobile_img: 'src/assets/images/mobile-image-hero-3.jpg'
    }
]

const currentIndex = ref(0)
const currentImage = ref(heroContent[currentIndex.value].desktop_img)
const currentImageMobile = ref(heroContent[currentIndex.value].mobile_img)
const currentAltText = ref(heroContent[currentIndex.value].title)

const btnLeft = ref(null)
const btnRight = ref(null)

const changeSlide = (increment) => {
    currentIndex.value = (currentIndex.value + increment + heroContent.length) % heroContent.length
    currentImage.value = heroContent[currentIndex.value].desktop_img
    currentImageMobile.value = heroContent[currentIndex.value].mobile_img
    currentAltText.value = heroContent[currentIndex.value].title
}

const handleKeyPress = (event) => {
  if (event.key === 'ArrowRight') {
    changeSlide(-1)
    const miBtn = btnRight.value
    miBtn.classList.add('keyboard')
    setTimeout(() => {
        miBtn.classList.remove('keyboard')
    }, 70);
  } else if (event.key === 'ArrowLeft') {
    changeSlide(1)
    const miBtn = btnLeft.value
    miBtn.classList.add('keyboard')
    setTimeout(() => {
        miBtn.classList.remove('keyboard')
    }, 70);
  }
}

onMounted(() => {
  window.addEventListener('keydown', handleKeyPress)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeyPress)
})
</script>

<template>
    <section class="hero">
        <article class="hero-image">
            <picture>
                <source media="(max-width: 520px)" :srcset="currentImageMobile">
                <img :src="currentImage" :alt="currentAltText">
            </picture>
        </article>
        <article class="hero-info">
            <h1 class="hero-info-title">{{ heroContent[currentIndex].title }}</h1>
            <p class="hero-info-text">{{ heroContent[currentIndex].content }}</p>
            <a class="hero-info-link" href="javascript:;">SHOP NOW
                <svg class="icon-arrow" width="40" height="12" xmlns="http://www.w3.org/2000/svg"><path d="M34.05 0l5.481 5.527h.008v.008L40 6l-.461.465v.063l-.062-.001L34.049 12l-.662-.668 4.765-4.805H0v-1h38.206l-4.82-4.86L34.05 0z" fill="#000" fill-rule="nonzero"/></svg>
            </a>
            <article class="nav">
                <button @click="changeSlide(-1)" ref="btnLeft" class="nav-prev">
                    <svg class="btn" width="14" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M13 0L1 12l12 12" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>
                </button>
                <button @click="changeSlide(1)" ref="btnRight" class="nav-next">
                    <svg class="btn" width="14" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M1 0l12 12L1 24" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>
                </button>
            </article>
        </article>
    </section>
</template>

<style scoped>
.hero {
    width: 100%;
    height: 534px;
    display: flex;
}
.hero-image {
    width: 100%;
    max-width: 840px;
    height: 100%;
}
.hero-info {
    width: 100%;
    max-width: 600px;
    height: 100%;
    padding: 7.55rem 0 0 6.3rem;
    position: relative;
    transition: .3s;
}
.hero-info-title {
    max-width: 400px;
    font-size: 3rem;
    font-weight: 500;
    line-height: 2.83rem;
    letter-spacing: -.1rem;
}
.hero-info-text {
    max-width: 400px;
    margin-top: 1.3rem;
    font-weight: 300;
    line-height: 1.38rem;
    color: var(--dark-gray);
}
.hero-info-link {
    display: inline-block;
    margin-top: 1.38rem;
    font-size: .97rem;
    font-weight: 500;
    text-decoration: none;
    color: var(--black);
    letter-spacing: .75rem;
    transition: .3s;
}

svg path {
    transition: .3s;
}
.hero-info-link:hover {
    color: var(--dark-gray);
    & svg path {
        fill: var(--dark-gray);
    }
}
.icon-arrow {
    position: relative;
    left: .2rem;
    top: .15rem;
}
.nav {
    position: absolute;
    bottom: 0;
    left: 0;
}
.nav-prev,
.nav-next {
    width: 80px;
    height: 80px;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    border: none;
    background-color: var(--black);
    cursor: pointer;
}
.nav-prev:hover,
.nav-next:hover {
    background-color: var(--very-dark-gray);
}
/* Mouse Click */
.nav-prev:active,
.nav-next:active {
    background-color: var(--black);
}
/* Keyboard Left Right */
.keyboard {
    background-color: var(--very-dark-gray);
}

img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
/* Media Query */
@media screen and (max-width: 1180px) {
    .hero {
        max-width: 840px;
        height: fit-content;
        flex-direction: column;
    }
    .hero-info {
        width: 100%;
        max-width: none;
        padding: 3rem 4rem 4rem;
    }
    .hero-info-title {
        max-width: none;
    }
    .hero-info-text {
        max-width: none;
    }
    .hero-info-link {
        margin-top: 2.5rem;
    }
    .nav {
        width: 100%;
        height: fit-content;
        display: flex;
        justify-content: flex-end;
        top: -80px;
    }
}

@media screen and (max-width: 768px) {
    .hero-info {
        padding: 4rem 2rem;
    }
}

@media screen and (max-width: 520px) {
    .nav {
        top: -60px;
    }
    .nav-prev,
    .nav-next {
        width: 60px;
        height: 60px;
    }
    .hero-info-title {
        max-width: none;
        font-size: 2.2rem;
        line-height: 2.5rem;
        letter-spacing: -.11rem;
    }
}
</style>