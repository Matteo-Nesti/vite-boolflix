<template>
    <div class="card-container">

        <img :src="getThumbimage(item.poster_path)" :alt="item.title || item.name" class="thumb">

        <ul>
            <li>
                <h4>
                    Titolo
                </h4>
            </li>
            <li> {{ item.title || item.name }} </li>
            <li>
                <h4 class="mt-2">
                    Titolo originale
                </h4>
            </li>
            <li> {{ item.original_title || item.original_name }} </li>
            <li>
                <h4>Lingua originale</h4>
            </li>
            <li class="my-3">
                <img :src="getImagePath(item.original_language)" :alt="item.original_language" class="lang">
            </li>
            <li>
                <h4>Voto</h4>
            </li>
            <li>
                <font-awesome-icon v-for="star in convertVote(item.vote_average).newRange" :icon="['fas', 'star']" class="stars" />
                <font-awesome-icon v-for="star in convertVote(item.vote_average).emptyStar" :icon="['far', 'star']" class="stars" />
            </li>
        </ul>
    </div>
</template>

<script>
const imageThumb = 'https://image.tmdb.org/t/p/'
export default {
    props: {
        item: Object,
        titleSection: String
    },
    data() {
        return {
        }
    },
    methods: {
        convertVote(vote) {
            const wholeNumber = Math.round(vote)
            const newRange = Math.ceil(wholeNumber / 2)
            const emptyStar = 5 - newRange
            return { newRange, emptyStar };
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
            if (!url) return 'https://catalog.osaarchivum.org/assets/thumbnail_placeholder_movie-480596e192e7043677f77cf78b13bdd1.jpg'
            return imageThumb + 'w342' + url
        },
    },
}
</script>
<style lang="scss" scoped>
.card-container {
    background-color: #000;
    position: relative;


}

.stars {
    color: rgb(255, 230, 0);
}

.card-container:hover ul {
    transition: .5s;
    opacity: 1;
}

.card-container:hover .thumb {
    transition: .5s;
    opacity: .4;
}

.lang {
    max-width: 50px;
}

.thumb {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

ul {
    list-style: none;
    position: absolute;
    top: 50px;
    left: 10px;
    opacity: 0;


}
</style>