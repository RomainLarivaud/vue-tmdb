<template>
    <div class="header">
            <div>
                <img id="logo-tmdb" src="../assets/images/tmdbLogo.svg" alt="logo_tmbd">
                <input type="search" name="" id="search-movie">
            </div>
            <div id="menuHeader">
                <a class="menuCategory">Popular</a>
                <a class="menuCategory">Playing</a>
                <a class="menuCategory">Upcoming</a>
            </div>
    </div>
</template>


<script>
// Import CSS
import "../styles/style.css"
import "../styles/header.css"

export default {
    name: 'Header'
}
</script>