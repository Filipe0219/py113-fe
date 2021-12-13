<template>
  <div>
    <section class="section">
        <b-button type="is-primary is-size-3 is-light" @click="search(1)">Load me that funny Joke!!!</b-button>
    </section>

    <div v-if="joke">
    <section class="section is-size-3" >
        {{ joke.question }}
    </section>
    <section class="section" v-if="joke.question">
        <b-button type="is-primary is-size-3" @click="show_answer = !show_answer">Tell me!</b-button>        
    </section>
    </div>
    <section class="section is-size-3" v-if="show_answer">
      {{ joke.answer }}
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
