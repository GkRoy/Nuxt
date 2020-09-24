<template>
  <div class="container">
    <h3>Post detail</h3>
    <b-card
      no-body
      style="max-width: 20rem"
    >
        <template v-slot:header>
        <h4 class="mb-0">{{ post.id }}</h4>
        </template>
      <b-card-body>
        <b-card-title>{{ post.title }}</b-card-title>
        <b-card-sub-title class="mb-2"></b-card-sub-title>
        <b-card-text>
            <h5>

          User ID: {{post.userId}}
            </h5>
          <div>
            {{ post.body }}
          </div>
        </b-card-text>
      </b-card-body>
    </b-card>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      post: {},
    };
  },
  async created() {
    try {
      const res = await axios.get(
        "https://jsonplaceholder.typicode.com/posts/" + this.$route.params.id
      );
      this.post = res.data;
    } catch (error) {
      console.error(error);
    }
  },
};
</script>