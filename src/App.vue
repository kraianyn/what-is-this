<template>
    <div id="container">
        <img src="./assets/logo.png">
        <div id="search-row">
            <input v-model.trim="entity" type="text" placeholder="будь-що у Всесвіті">
            <button @click="findArticles">знайти статті</button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'App',
    methods: {
        findArticles() {
            console.log(this.entity);
        }
    }
}

</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Special+Elite&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@300&display=swap');

* {
    padding: 0;
    margin: 0;
}

body {
    background: #333;
}

#container {
    width: 40%;
    margin: 5% auto;
}

img {
    width: 50%;
    display: block;
    margin: 0 auto;
}

#search-row {
    display: flex;
    gap: 3%;
    justify-content: center;
    flex-wrap: wrap;
    margin-top: 10%;
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
    box-shadow: inset 0 0 5px 0 #000;
}
input::placeholder {
    color: #aaa;
}

button {
    flex-grow: 1;
    box-shadow: 0 0 5px 0 #111;
}
button:hover {
    cursor: pointer;
    background-color: #555;
}

</style>
