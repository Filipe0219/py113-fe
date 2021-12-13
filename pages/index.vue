<template>
  <div>
    <section class="section">
      Welcome to our Dad Jokes Website.

      <div>
        <b-button type="is-primary is-light" @click="search(1)">Load me tha funny Joke!!!</b-button>
      </div>
    </section>

    <section v-if="joke">
      <div>
        {{ joke.question }}
      </div>
      <div>
        <b-button type="is-secondary is-light" @click="show_answer = !show_answer">Tell me!</b-button>        
      </div>
      <div v-if="show_answer">
        {{ joke.answer }}
      </div>

    </section>
  </div>
</template>

<script>
export default {
    data() {
      return {
        joke: {},
        show_answer: false
      }
    },
    methods: {
      reset() {
        this.joke = {};
        this.show_answer = false;
      },
      async search(page=1) {
        this.reset();
        const response = await this.$axios.$get("https://hh-jokes-api.herokuapp.com/random")
        console.log(response)
        this.joke = response;
      },
    }
}
</script>
