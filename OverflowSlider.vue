<script setup>
import {
    usePage
} from '@inertiajs/vue3'
import {
    ref,
    onMounted
} from 'vue';
import {
    Splide,
    SplideSlide
} from '@splidejs/vue-splide';
import '@splidejs/splide/dist/css/themes/splide-default.min.css';

const colors = ['#E8DCFA', '#FFF3CF', '#FFDA6E'];

const slides = [{
        id: 1,
        description: "Start a project management career with our industry-recognized, accredited online courses.",
        image: 'https://images.prismic.io/360learning/60223329-28c2-47c2-9f90-9d83a1950500_website_quote_KristinTrujeque.jpg?fit=max&fm=png&q=75&dpr=1&auto=format&h=64&w=64&mask=ellipse',
        name: "John Smith",
        country: "United States",
        bgColor: colors[0]
    },
    {
        id: 2,
        description: "Gain essential business skills with our Ofqual-regulated Business and Management Training.",
        image: 'https://images.prismic.io/360learning/60223329-28c2-47c2-9f90-9d83a1950500_website_quote_KristinTrujeque.jpg?fit=max&fm=png&q=75&dpr=1&auto=format&h=64&w=64&mask=ellipse',
        name: "Emma Johnson",
        country: "United Kingdom",
        bgColor: colors[1]
    },
    {
        id: 3,
        description: "Enhance your teaching career with accredited courses for diverse, rewarding opportunities.",
        image: 'https://images.prismic.io/360learning/60223329-28c2-47c2-9f90-9d83a1950500_website_quote_KristinTrujeque.jpg?fit=max&fm=png&q=75&dpr=1&auto=format&h=64&w=64&mask=ellipse',
        name: "Michael Brown",
        country: "Canada",
        bgColor: colors[2]
    },
    {
        id: 4,
        description: "Gain comprehensive accounting skills with accredited courses covering finance, taxes, and software.",
        image: 'https://images.prismic.io/360learning/60223329-28c2-47c2-9f90-9d83a1950500_website_quote_KristinTrujeque.jpg?fit=max&fm=png&q=75&dpr=1&auto=format&h=64&w=64&mask=ellipse',
        name: "Sarah Davis",
        country: "Australia",
        bgColor: colors[0]
    },
    {
        id: 5,
        description: "Excel in office administration and receptionist roles with our accredited, career-advancing programs.",
        image: 'https://images.prismic.io/360learning/60223329-28c2-47c2-9f90-9d83a1950500_website_quote_KristinTrujeque.jpg?fit=max&fm=png&q=75&dpr=1&auto=format&h=64&w=64&mask=ellipse',
        name: "David Wilson",
        country: "New Zealand",
        bgColor: colors[1]
    },
    {
        id: 6,
        description: "Boost your hospitality career with accredited tourism courses for a lucrative future.",
        image: 'https://images.prismic.io/360learning/60223329-28c2-47c2-9f90-9d83a1950500_website_quote_KristinTrujeque.jpg?fit=max&fm=png&q=75&dpr=1&auto=format&h=64&w=64&mask=ellipse',
        name: "Lisa Chen",
        country: "Singapore",
        bgColor: colors[2]
    },
];


const contentSplideOptions = {
    type: "slide",
    autoplay: false,
    focus: 'center',
    wheel: true,
    releaseWheel: true,
    autoWidth: true,
    trimSpace: false,
    arrows: false,
    pagination: false,
    gap: "1rem",
    perMove: 1,
    interval: 3000,
};

const splideRef = ref(null);
const progress = ref(0);

const prevSlide = () => {
    splideRef.value?.go('-1');
};

const nextSlide = () => {
    splideRef.value?.go('+1');
};

const onMoved = (splide) => {
    const totalSlides = splide.length;
    const currentIndex = splide.index;
    progress.value = ((currentIndex + 1) / totalSlides) * 100;
};

onMounted(() => {
    if (splideRef.value) {
        splideRef.value.splide.on('mounted move', () => {
            const splide = splideRef.value.splide;
            const end = splide.length;
            const rate = Math.min((splide.index + 1) / end, 1);
            progress.value = rate * 100;
        });
    }
});
</script>

<template>
    <section class="mt-32 md:mt-[132px]">
        <div class="container">
            <div class="">
                <h1 class="text-xl sm:text-4xl font-bold text-black-500 text-center mx-auto">Client Testimonials</h1>
                <p class="mt-9 md:mt-10 text-lg sm:text-2xl font-normal text-black-900 text-center xl:max-w-[59ch] mx-auto">Hear Heart-warming Stories from Our Valued Customers Sharing Their Experience and Success with Our Services</p>
            </div>
        </div>
        <div :style="{ 'background-image': $page.props.assetURL ? 'url(' + $page.props.assetURL + '/web-assets/clientSection-background.png)' : 'url(../../web-assets/clientSection-background.png)' }"  class="mt-25 clientSection-background">
            <div class="">
                <Splide :options="contentSplideOptions" @moved="onMoved" ref="splideRef" class="">
                    <SplideSlide v-for="(slide, index) in slides" :key="index" class="">
                        <div class="rounded-xl shadow-soft-shadow w-[350px] sm:w-[467px] py-10 px-5 my-2" :style="{ backgroundColor: slide.bgColor }">
                            <div class="flex items-center gap-4">
                                <img loading="lazy" :src="slide.image" alt="image" class="w-16 h-16 block flex-shrink-0 max-w-full rounded-full">
                                <div class="flex flex-col">
                                    <p class="text-xl sm:text-[26px] font-semibold text-black-900 overflow-hidden name-lineclamp">{{ slide.name }}</p>
                                    <p class="text-lg sm:text-[22px] font-normal text-black-900 overflow-hidden">{{ slide.country }}</p>
                                </div>
                            </div>
                            <div class="mt-9 md:mt-[54px] h-[54px]">
                                <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/reviewSliderSvg.svg' : '../../web-assets/reviewSliderSvg.svg'" alt="svg" class="">
                            </div>
                            <div class="block">
                                <p class="mt-2 text-xl sm:text-[22px] font-normal text-black-900 overflow-hidden h-36 description-lineClamp">{{ slide.description }}</p>
                            </div>
                            <div class="mt-8 md:mt-9">
                                <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/trustpilot.svg' : '../../web-assets/trustpilot.svg'" alt="trustpilot svg" class="">
                            </div>
                        </div>
                    </SplideSlide>
                </Splide>
            </div>
            <div class="container">
                <div class="block flex items-center justify-between py-4 md:py-14 w-full lg:w-3/5 mx-auto">
                    <button class="prev" @click="prevSlide">
                        <i class="fas fa-chevron-left text-black-400 bg-white rounded-10 w-[35px] h-[35px] xl:w-[50px] xl:h-[50px] flex justify-center items-center"></i>
                    </button>
                    <div class="my-slider-progress w-full mx-4">
                        <div class="my-slider-progress-bar" :style="{ width: `${progress}%` }"></div>
                    </div>
                    <button class="next" @click="nextSlide">
                        <i class="fas fa-chevron-right text-black-400 bg-white rounded-10 w-[35px] h-[35px] xl:w-[50px] xl:h-[50px] flex justify-center items-center"></i>
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>

.name-lineclamp{
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
}

.description-lineClamp{
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 5;
    -webkit-box-orient: vertical;
}

.my-slider-progress {
    background: #A4A4A4;
    height: 4px;
}

.my-slider-progress-bar {
    background: white;
    height: 4px;
    transition: width 400ms ease;
    width: 0;
}
</style>