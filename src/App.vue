<template>
    <my_nav class="d-none d-lg-flex"></my_nav>
    <my_nav_phone></my_nav_phone>
    <div class="my-5"></div>
    <div
        class="d-flex flex-column-reverse flex-lg-row alen jen gap gap-lg-0 gap-5"
    >
        <hero_text></hero_text>
        <div class="mx-3"></div>
        <div class="my-5 d-none d-lg-block"></div>
        <div class="d-none d-lg-block my-5"></div>
        <div
            style="
                min-width: 300px;
                aspect-ratio: 1/1;
                background-image: url(assets/hero_image.png);
            "
            class="rounded-3 bg-light bg-img"
        ></div>
    </div>

    <br />
    <br />
    <br />
    <br />

    <p class="fw-bold my-4 f-24 text-light">Games</p>

    <div id="normal_games" class="fow jen flex-wrap gap-2">
        <normal_game
            v-for="item in normal_game_list"
            :tittle="item.title"
            :genre="item.genre"
            :dev="item.developer"
            :image="item.thumbnail"
        ></normal_game>
    </div>

    <p class="fw-bold my-4 f-24 text-light">Trending Games</p>

    <div class="fow flex-wrap gap-1 jen">
        <trend_game
            v-for="game in trend_game_list"
            :tittle="game.title"
            :image="game.thumbnail"
        ></trend_game>
    </div>

    <p class="fw-bold my-4 f-24 text-light">Reccomended Games</p>

    <div
        data-recom
        style="max-width: 700px; aspect-ratio: 1/0.8"
        class="auto d-flex flex-column m-auto flex-lg-row p-2"
    >
        <div class="w-lg-50 w-100 h-50 h-lg-100 p-1">
            <reco_game
                :tittle="reco_game_list[0]?.title"
                :image="reco_game_list[0]?.thumbnail"
                :desc="reco_game_list[0]?.short_description"
                :platform="reco_game_list[0]?.platform"
                :genre="reco_game_list[0]?.genre"
                :dev="reco_game_list[0]?.developer"
            ></reco_game>
        </div>
        <div class="flex-grow-1 d-flex flex-lg-column flex-column p-1 gap-1">
            <reco_game_v2
                class="flex-grow-1"
                :tittle="reco_game_list[1]?.title"
                :image="reco_game_list[1]?.thumbnail"
                :genre="reco_game_list[1]?.genre"
            ></reco_game_v2>
            <reco_game_v2
                class="flex-grow-1"
                :tittle="reco_game_list[2]?.title"
                :image="reco_game_list[2]?.thumbnail"
                :genre="reco_game_list[2]?.genre"
            ></reco_game_v2>
        </div>
    </div>

    <p class="fw-bold my-4 f-24 text-light">Games By Genre</p>

    <div class="d-flex flex-column flex-lg-row gap-5">
        <div class="fol flex-grow-1 gap-2">
            <p class="text-light f-12 fw-bold">Shooter</p>
            <div class="fol gap-1">
                <game_by_genre
                    v-for="game in genre_1_list"
                    :tittle="game.title"
                    :desc="game.short_description"
                    :image="game.thumbnail"
                ></game_by_genre>
            </div>
        </div>
        <div class="fol flex-grow-1 gap-2">
            <p class="text-light f-12 fw-bold">Strategy</p>
            <div class="fol gap-1">
                <game_by_genre
                    v-for="game in genre_2_list"
                    :tittle="game.title"
                    :desc="game.short_description"
                    :image="game.thumbnail"
                ></game_by_genre>
            </div>
        </div>
        <div class="fol flex-grow-1 gap-2">
            <p class="text-light f-12 fw-bold">MMORPG</p>
            <div class="fol gap-1">
                <game_by_genre
                    v-for="game in genre_3_list"
                    :tittle="game.title"
                    :desc="game.short_description"
                    :image="game.thumbnail"
                ></game_by_genre>
            </div>
        </div>
    </div>
    <div class="my-5"></div>
    <p class="text-light text-center">Piyan Apriyanto ©2025</p>
    <p class="text-center text-light">
        API provider by <a href="https://www.freetogame.com/">FreeToGame.com</a>
    </p>
</template>

<script setup>
import { onMounted, ref, computed } from "vue";
import axios from "axios";
import s_res from "./components/search_result.vue";
import game_by_genre from "./components/game_by_genre.vue";
import normal_game from "./components/normal_game.vue";
import options from "./components/options.vue";
import subs from "./components/subscribe.vue";
import news from "./components/news.vue";
import reco_game from "./components/reco_game.vue";
import reco_game_v2 from "./components/reco_game_v2.vue";
import hero_text from "./components/hero_text.vue";
import my_nav from "./components/nav.vue";
import my_nav_phone from "./components/nav_phone.vue";
import trend_game from "./components/trend_game.vue";

var normal_game_list = ref([]);
var trend_game_list = ref([]);
var reco_game_list = ref([]);
var genre_1_list = ref([]);
var genre_2_list = ref([]);
var genre_3_list = ref([]);

var genres = [genre_1_list, genre_2_list, genre_3_list];

async function get_genre(id, genre) {
    const request = await fetch("data/games.json");
    const data = await request.json();
    const max = 5;
    var _current_taken = 0;
    for (let i = 0; i < 400; i++) {
        if (data[i].genre == genre) {
            genres[id].value.push(data[i]);
            _current_taken += 1;
        }
        if (_current_taken >= max) {
            return;
        }
    }
}

async function get_data() {
    const request = await fetch("data/games.json");
    const data = await request.json();

    //get normal game
    for (let i = 0; i < 10; i++) {
        normal_game_list.value.push(data[Math.floor(Math.random() * 403)]);
    }
    //get trend game
    for (let i = 0; i < 6; i++) {
        trend_game_list.value.push(data[Math.floor(Math.random() * 403)]);
    }
    //get_reco_game
    for (let i = 0; i < 3; i++) {
        reco_game_list.value.push(data[Math.floor(Math.random() * 403)]);
    }
}

onMounted(() => {
    get_data();
    get_genre(0, "Shooter");
    get_genre(1, "Strategy");
    get_genre(2, "MMORPG");
});
</script>

<!-- -->

<style scoped>
@media screen and (max-width: 992px) {
    [data-recom] {
        max-width: 500px !important;
    }
}
@media screen and (min-width: 992px) {
    [data-recom] {
        aspect-ratio: 600/250 !important;
    }
}
</style>
