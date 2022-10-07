<template>
   <div class="card-generate">
        <img v-if="insertCard.poster_path"
            :src="`https://image.tmdb.org/t/p/w342${insertCard.poster_path}`"
            :alt="insertCard.title ? insertCard.title : insertCard.name">
        <img v-else
        src="https://www.altavod.com/assets/images/poster-placeholder.png"
        :alt="`Copertina ${insertCard.title ? insertCard.title : insertCard.name}`">
        
        <div class="card-content">
            <h3>
                <small>Title: </small> {{ insertCard.title ? insertCard.title : insertCard.name }}
            </h3>
            <h5>
                <small>Original Title: </small> {{ insertCard.original_title ? insertCard.original_title : insertCard.original_name }}
            </h5>
            <small>overview:</small>
            <p>
                {{ insertCard.overview ? insertCard.overview : '' }}
            </p>
            <div class="flags-language">
                <small>  
                    Language: 
                </small>

                <img v-if="flagsLanguage.includes(insertCard.original_language)"
                :src="require(`../assets/img/${insertCard.original_language}.svg`)" 
                :alt="`lang ${insertCard.original_language}`">

                <p v-else>
                    {{ insertCard.original_language }}
                </p>
            </div>
            <div class="star">
                <i v-for="vote in 5" :key="vote"
                    class="fa-star"
                    :class="(vote <= addStar()) ? 'fa-solid' : 'fa-regular'">
                </i>
            </div>
        </div>
   </div>
</template>

<script>
export default {
    name: "MyCard",
    props: {
        insertCard: Object
    },
    data() {
        return {
            flagsLanguage: [
                'it',
                'en'
            ]
        }
    },
    methods: {
        getTitle() {
            if(this.insertCard.title) {
                return this.insertCard.title;
            } else {
                return this.insertCard.name;
            }
        },
        getOriginalTitle() {
            if(this.insertCard.original_title) {
                return this.insertCard.original_title;
            } else {
                return this.insertCard.original_name;
            }
        },
        addStar() {
            return Math.ceil(this.insertCard.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" scoped>
.card-generate {
    position: relative;
    display: inline-block;
    padding: 5px;
    width: 342px;
    height: 513px;
    
    img {
        max-width: 100%;
        height: 60vh;
        object-fit: cover;

        &:hover {
            filter: grayscale(70%);
            opacity: 6%;
        }
    }

    .card-content {
        display: none;
        position: absolute;
        top: 0;
        left: 0;
        transform: translate(0, 5%);
        padding: 25px;
        width: 100%;
        height: 20px;

        h3, h5, p {
            padding-bottom: 10px;
        }

        p {
            font-size: .8rem;
            text-align: left;
            line-height: 20px;
        }

        small {
            font-style: oblique;
            line-height: .8rem;
        }

        .flags-language {
            display: flex;
            justify-content: center;
            gap: 8px;
            font-size: .7rem;

            img {
                max-width: 100%;
                height: .8rem;
            }   
        }
    }

    &:hover .card-content {
        display: block;
        color: #ffffff;  
        pointer-events: none; 
    }
}
</style>