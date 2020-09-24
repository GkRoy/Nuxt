<template>
    <b-list-group-item :to="'/posts/' + id">
        {{ id }} - {{ title }}
    </b-list-group-item>
</template>

<script>
export default {
    name: 'Post',
    props: ['id', 'title']
}
</script>