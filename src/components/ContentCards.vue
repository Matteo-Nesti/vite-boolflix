<template lang="">
    <ul>
        <li> {{ item.title || item.name}} </li>
        <li> {{ item.original_title || item.original_name}} </li>
        <li>
            <img 
            :src="getImagePath(item.original_language)" 
            :alt="item.original_language">
        </li>
        <li>
            <img 
            :src="getThumbimage(item.poster_path)" 
            :alt="item.title || item.name">
        </li>
        <li> {{ convertVote(item.vote_average) }} </li>
      </ul>
</template>

<script>
const imageThumb = 'https://image.tmdb.org/t/p/'
export default {
    props: {
        item: Object,
    },
    data() {
        return {
        }
    },
    methods: {
        convertVote(vote) {
            const wholeNumber = Math.round(vote)
            const newRange = Math.ceil(wholeNumber / 2)
            if (newRange == 4) {
                return '<font-awesome-icon icon="fa-solid fa-star" />'
            }
            return newRange;
        },

        getImagePath(lang) {
            if (lang === 'it') {
                return '../src/assets/img/it.png'
            }
            else if (lang === 'en') {
                return '../src/assets/img/en.png'
            }
            else {
                return lang
            }
        },
        getThumbimage(url) {
            return imageThumb + 'w342' + url
        },
    },
}
</script>
<style lang="">
    
</style>