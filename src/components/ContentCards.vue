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
        <li> {{ item.vote_average}} </li>
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
        getImagePath(lang) {
            if (lang === 'it') {
                return '../src/assets/img/it.png'
            }
            else if (lang === 'en') {
                return '../src/assets/img/en.png'
            }
            else {
                return ''
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