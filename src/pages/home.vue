
<template>
  <v-container>
    <v-card>
      <v-card-text v-if="jokes.length > 0">
        <v-list v-for="joke in jokes" :key="joke.id">
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>
                <v-list-item-subtitle v-if="joke.url">
                  <v-chip x-new href="joke.url" target="_blank" rel="noopener noreferrer">
                    {{ joke.value }}
                  </v-chip>
                </v-list-item-subtitle>
                <v-list-item-subtitle v-else>
                  {{ joke.value }}
                </v-list-item-subtitle>
              </v-list-item-title>
              <v-list-item-action>
                <v-btn icon small color="red" @click="deleteJoke(joke.id)">
                  <v-icon>mdi-delete</v-icon>
                </v-btn>
              </v-list-item-action>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-card-text>
      <v-card-text v-else>
         <v-alert>No jokes here!</v-alert>
      </v-card-text>
    </v-card>
    <v-card-text>
        <div class="d-flex justify-center">
          <v-btn style="background-color:#004D40;" @click="addJoke">Get a new Joke</v-btn>
        </div>
      </v-card-text>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      jokes: [],
    };
  },

  methods: {
    async addJoke() {
      try {
        const res = await axios.get('https://api.chucknorris.io/jokes/random');
        this.jokes.push(res.data);
      } catch (error) {
        console.log(error);
      }
    },
    deleteJoke(id) {
      this.jokes = this.jokes.filter(j => j.id !== id);
    },
    clearJokes() {
      this.jokes = [];
    },
  },
};
</script>

<style scoped>
.d-flex {
  display: flex;
}
.justify-space-between {
  justify-content: space-between;
}
</style>
