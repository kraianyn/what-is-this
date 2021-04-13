<template>
    <div id="container">
        <img :style="{'animation': logoAnimation}" src="./assets/logo.png">
        <div id="search-row">
            <input @keyup="updateButton" v-model.trim="entity" type="text" placeholder="будь-що у Всесвіті">
            <button @click="findArticles" :style="{'display': buttonDisplay}">знайти статті</button>
        </div>
        <div id="articles">
            <ArticleLink v-for="article in articles" :key="article.id" :text="article.title" :link="article.link"/>
        </div>
    </div>
</template>

<script>
import ArticleLink from './components/ArticleLink.vue'
const axios = require('axios');

const LOGO_OUT_DURATION_S = .7;  // duration (in seconds) of the animation applied to the logo before the search results are shown

export default {
    name: 'App',
    components: {ArticleLink},
    data() {
        return {
            buttonDisplay: 'none',
            logoAnimation: 'none',
            articles: []
        }
    },
    methods: {
        updateButton() {
            this.buttonDisplay = this.entity ? 'inline-block' : 'none';
        },
        findArticles() {
            // if the search box is not empty (although the button should be hidden if it is, there may be a tiny delay)
            if (!this.entity) {
                return;
            }

            let request = `${location.protocol}//en.wikipedia.org/w/api.php?origin=*&action=opensearch&format=json&search=${encodeURIComponent(this.entity)}`;
            axios.get(request).then((response) => {
                let displayDelay = 0;  // no delay unless it is the first search
                if (this.logoAnimation == 'none') {  // if no searches have been made yet
                    this.logoAnimation = `${LOGO_OUT_DURATION_S}s forwards logoOut`;  // makes the logo escape, freeing the space for the search results
                    displayDelay = LOGO_OUT_DURATION_S * 1000;  // delay (in milliseconds) until after the logo has escaped
                }

                setTimeout(() => {
                    this.articles = [];
                    response.data[1].forEach((articleTitle, articleIndex) => {
                        this.articles.push({
                            id: articleIndex,
                            title: articleTitle,
                            link: response.data[3][articleIndex]
                        });
                    });
                }, displayDelay)
            }).catch(error => console.error(error));
        }
    }
}

</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Special+Elite&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@300&display=swap');

:root{
    --container-margin-top: 15vh;
    --logo-height: 50vh;
    --inner-shadow: inset 0 0 5px 0 #000;
}

* {
    padding: 0;
    margin: 0;
}

body {
    background: #333;
}

#container {
    font: 1.2rem 'Raleway', arial;
    width: 60%;
    margin: var(--container-margin-top) auto 0;
}

img {
    height: var(--logo-height);
    display: block;
    margin: 0 auto;
}

@keyframes logoOut {
    to {
        margin-top: calc((var(--container-margin-top) + var(--logo-height)) * -1);
    }
}

#search-row {
    display: flex;
    gap: 3%;
    justify-content: center;
    flex-wrap: wrap;
    margin-top: 10vh;
}

input, button {
    background-color: #444;
    font: 1.2rem 'Raleway', arial;
    letter-spacing: .05em;
    color: #fff;
    text-align: center;
    padding: .8rem 1rem;
    border: none;
    transition: all .15s;
}
input:focus, button:focus {
    outline: #9ad solid 3px;
    box-shadow: none;
}

input {
    flex-grow: 8;
    box-shadow: var(--inner-shadow);
}
input::placeholder {
    color: #aaa;
}

button {
    white-space: nowrap;
    flex-grow: 1;
    box-shadow: 0 0 5px 0 #111;
}
button:hover {
    cursor: pointer;
    background-color: #555;
}

#articles {
    margin-top: 8vh;
}

</style>
