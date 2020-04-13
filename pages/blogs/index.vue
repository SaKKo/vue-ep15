<template lang="html">
  <div>
    Blogs !!!!! Required login
    <v-btn :to="{ name: 'blogs-new' }"> New Blog </v-btn>
    <v-card
      v-for="blog in blogs"
      :key="blog.id"
      class="mx-auto"
      max-width="344"
      style="margin-top: 10px;"
    >
      <v-card-text>
        <p class="display-1 text--primary">
          {{ blog.title }}
        </p>
        <div class="text--primary">blog id: {{ blog.id }}</div>
      </v-card-text>
      <v-card-actions>
        <v-btn
          :to="{ name: 'blogs-id', params: { id: blog.id } }"
          text
          color="deep-purple accent-4"
        >
          Learn More
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
import * as BlogsApi from '@/utils/blogsApi'
export default {
  middleware: 'auth',
  data() {
    return {
      blogs: []
    }
  },
  async mounted() {
    const response = await BlogsApi.index()
    console.log('RESPONSE', response)
    this.blogs = response.data
  }
}
</script>

<style lang="css" scoped></style>
