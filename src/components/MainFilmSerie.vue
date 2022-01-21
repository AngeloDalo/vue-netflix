<template>
    <li class="col-xl-3 col-lg-4 col-md-5 col-sm-6 mb-5">
        <div class="container-card">
            <div class="div imgFilm">
                <img class="front-img"
                :src="srcImg"
                :alt="altImg">
            </div>
            <div class="div imgHover text-start p-2">
                <h1> {{ title }} </h1>
                <h2> {{ originalTitle }} </h2>
                <div class="div">
                    <i class="fas fa-star yellow" v-for="(i, index) in  vote" :key="index+title"></i>
                    <i class="fas fa-star grey" v-for="(i, index) in  (5-vote)" :key="index+title+i"></i>
                </div>
                <img class="flag-image"
                :src="src"
                :alt="alt">
                <p class="overview"> {{ overview }} </p>
            </div>
        </div>
    </li>
</template>

<script>
export default {
    name: "MainFilmSerie",
    props: ['src', 'alt', 'title', 'originalTitle', 'language', 'vote', 'srcImg', 'altImg', 'overview'],
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
li {
    .container-card {
        border: 2px solid white;
        height: 350px;
        &:hover .imgHover {
            display: block;
        }
        &:hover .imgFilm {
            display: none;
        }
        .imgHover {
            display: none;
            height: 100%;
            background-color: black;
            overflow: hidden;
            h1 {
                font-size: 1.3em;
            }
            h2 {
                font-size: 0.8em;
            }
            h3 {
                font-size: 0.7em;
            }
            h4 {
                font-size: 0.7em;
            }
            h1, h2, h3, h4 {
                color: white;
            }
            .yellow {
                color: yellow;
            }
            .grey {
                color: grey;
            } 
            .overview {
                color: white;
                font-size: 0.8em;
            }       
        }
        .imgFilm {
            height: 100%;
            width: 100%;
            .front-img {
                width: 100%;
                height: 100%;
                color: white;
            }        
        }
    }
}
.flag-image {
    width: 40px;
}
</style>