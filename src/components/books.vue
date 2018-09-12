 /* eslint-disable */ /* eslint-disable */

<template>
    <div class="booksCard">
        <h1>{{bookTitle}}</h1>
    </div>
</template>

<script>
    export default {
        name: "booksCard",

        props: {
            bookTitle: String,
            bookGenre: String,
            bookDescription: String,
            bookCoverUrl: String,
        }
    }

</script>