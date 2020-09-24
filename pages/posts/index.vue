<template>
    <div class="container">
        <h3>Posts</h3>
        <b-list-group>
            <Post 
                v-for="post of posts"
                :key = "post.id"
                :id = "post.id"
                :title = "post.title"
            />
        </b-list-group>
    </div>
</template>

<script>
import axios from 'axios';
import Post from '../../components/Post'

export default {
    components: {
        Post
    },

    data() {
        return {
            posts: []
        }
    },

    async created() {
        try {
            const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
            this.posts = res.data;

            const problems = await axios.get("https://api-test.comunal.co/problem");
            console.log(problems)
        } catch (error) {
            console.error(error)
        }
    }
}
</script>