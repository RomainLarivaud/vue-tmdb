<template>
    <div class="part-last-upcoming" v-if="is_data_fetched"> 
        <h2>Now Playing</h2>
        <div class="all-last-upcoming" v-if="is_data_fetched">
            <div class="upcmoing-case" :key="index" v-for="(film, index) in films.data.results.slice(0,8)" >
                <img v-bind:src="'https://image.tmdb.org/t/p/w500' + film.poster_path" alt="">
                <div class='info-upcoming'>
                    <h2>{{film.original_title}}</h2>
                    <span v-bind:data-vote="film.vote_average" class="star-container">
                        <div class="star-border"><div class="star"><div class="star-fill"></div></div></div>
                        <div class="star-border"><div class="star"><div class="star-fill"></div></div></div>
                        <div class="star-border"><div class="star"><div class="star-fill"></div></div></div>
                        <div class="star-border"><div class="star"><div class="star-fill"></div></div></div>
                        <div class="star-border"><div class="star"><div class="star-fill"></div></div></div>
                    </span>
                </div>
                <p class="number-upcoming">{{index+1}}</p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import $ from 'jquery';

// Import CSS
import "../styles/style.css"
import "../styles/home.css"

const keyApi = "aa212f6d5e1da31a4142d73f425783b1";
const urlApi = "https://api.themoviedb.org/3/";
const language = "en-EN";

export default {
    name: 'Latest',
    data (){
        return{
            films : null,
            is_data_fetched : false
        }
    },
    mounted() {
        axios
        .get (urlApi + "movie/now_playing?api_key=" + keyApi + "&language=" + language + "&page=1")
        .then((response) => {
            this.films = response;
            this.is_data_fetched = true;
        })
    }
}

export function getImage(size, path) {
    return 'https://image.tmdb.org/t/p/w' + size + path;
}

$(document).ready(function()
{

    $('.star-container').each(function()
    {
        var vote = $(this).data('vote');
        console.log(vote);
        if(vote <= 2)
        {
            $(this).find('.star-border:first-of-type .star-fill').css('width',vote*50+'%');
        }
        else if(vote > 2 && vote <= 4)
        {
            $(this).find('.star-border:first-of-type .star-fill').css('width','100%');
            $(this).find('.star-border:nth-of-type(2) .star-fill').css('width',(vote-2)*50+'%');
        }
        else if(vote > 4 && vote <= 6)
        {
            $(this).find('.star-border:first-of-type .star-fill, .star-border:nth-of-type(2) .star-fill').css('width','100%');
            $(this).find('.star-border:nth-of-type(3) .star-fill').css('width',(vote-4)*50+'%');
        }
        else if(vote > 6 && vote <= 8)
        {
            $(this).find('.star-border:first-of-type .star-fill, .star-border:nth-of-type(2) .star-fill, .star-border:nth-of-type(3) .star-fill').css('width','100%');
            $(this).find('.star-border:nth-of-type(4) .star-fill').css('width',(vote-6)*50+'%');
        }
        else if(vote > 8 && vote <= 10)
        {
            $(this).find('.star-border .star-fill').css('width','100%');
            $(this).find('.star-border:nth-of-type(5) .star-fill').css('width',(vote-8)*50+'%');
            console.log($(this).find('.star-border:nth-of-type(5) .star-fill'))
        }
    })
});

</script>