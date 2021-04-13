<template>
    <a :href='link' target="_blank">{{text}}</a>
</template>

<script>
export default {
    name: 'ArticleLink',
    props: {
        text: String,
        link: String
    }
}
</script>

<style scoped>
a {
    font-style: strong;
    letter-spacing: .05em;
    color: #fff;
    text-decoration: none;
    display: block;
    background-color: #444;
    padding: 1rem 1rem;
    box-shadow: var(--inner-shadow);
    border: none;
    margin: 1.5vh 0;
    transition: .3s background-color;
}
a:hover {
    background-color: #4d4d4d;
}
</style>
