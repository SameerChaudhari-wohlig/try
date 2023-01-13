<template>
  <v-app id="inspire">
    <v-app-bar color="cyan-lighten-1">
      <v-toolbar-title>Instagram </v-toolbar-title>
        <nuxt-link class="edit" to="/"><v-btn>Home</v-btn></nuxt-link>
      <nuxt-link class="edit" to="/home"><v-btn>User</v-btn></nuxt-link>
      <nuxt-link class="edit" to="/about"><v-btn>About</v-btn></nuxt-link>
      <v-text-field placeholder="Search ..." v-model="search"></v-text-field>
    </v-app-bar>
    <v-main class="bg-grey-lighten-2">
      <v-container fluid>
        <v-row>
          <v-col cols="12" md="12">
            <v-row>
              <v-col
                v-for="post in filteredProducts"
                :key="post.id"
                cols="12"
                md="4"
                sm="6"
                lg="3"
              >
                <v-card class="mx-auto">
                  <!-- <v-img :src="post.node.edge_sidecar_to_children.edges[0].node

                  .edge_media_to_tagged_user.edges[0].node.user.profile_pic_url" height="200px" cover></v-img> -->

                  <v-card-title>{{ post.node.full_name }} </v-card-title>
                  <v-img :src="post.node.image"></v-img>

                  <v-card-title>{{ post.node.username }} </v-card-title>

                  <!-- <v-card-subtitle> {{ Product.Price }} </v-card-subtitle> -->

                  <v-btn icon="mdi-cards-heart"></v-btn>

                  <v-btn icon="mdi-comment"></v-btn>

                  <v-btn icon="mdi-share"></v-btn>

                  <v-card-actions>
                    <v-btn color="orange-lighten-2" variant="text">
                      Read More..
                    </v-btn>

                    <!-- <v-card-title v-for="(post, i) in filteredposts" :key="i"> {{ post.node.full_name }} </v-card-title>  -->
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import data from "../data";

const Products = ref(data);
const search = ref("");

let posts = ref([]);
posts = data.body.edge_liked_by.edges;
// console.log(posts, "post ove");

// const url =
//   "https://instagram47.p.rapidapi.com/public_post_likers?shortcode=CHLXcX-h-Px";
// const options = {
//   method: "GET",
//   headers: {
//     "X-RapidAPI-Key": "ad8b4ad4b9mshae7a0a0393e1946p1f42b9jsn3d69d120c87b",
//     "X-RapidAPI-Host": "instagram47.p.rapidapi.com",
//     "Content-Type": "application/json",
//   },
// };

// const { data, pending, error, refresh } = await useFetch(url, options);
// console.log(ref([data._value]), "data from response");
// if (error) {
//   console.log(error);
// }
// posts = data._value[0].body.edge_liked_by.edges || [];

// const filteredProducts = computed(() => {
//   if (search.value) {
//     // console.log("inside if");
//     return [...posts].filter((item) => {
//       return search.value
//         .toLocaleLowerCase()
//         .split(" ")
//         .every((v) => item.node.full_name.toLocaleLowerCase().includes(v));
//     });
//   } else {
//     // console.log("inside else");
//     return posts;
//   }
// });

const filteredProducts = computed(() => {
  if (search.value) {
    // console.log("inside if");
    return [...posts].filter((item) => {
      return search.value
        .toLocaleLowerCase()
        .split(" ")
        .every((v) => item.node.full_name.toLocaleLowerCase().includes(v));
    });
  } else {
    // console.log("inside else");
    return posts;
  }
});
// console.log(filteredProducts, "FP");

fetch;
</script>

<style>
.edit {
  text-decoration: none;
  color: black;
}
</style>
