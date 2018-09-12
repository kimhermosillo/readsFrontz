 /* eslint-disable */

<template>
    <div class="authorsCard">
        <h1>{{bookTitle}}</h1>
    </div>
</template>

<script>
    export default {
        name: "authorsCard",

        props: {
            authFirst: String,
            authLast: String,
            authBio: String,
        }
    }

</script>