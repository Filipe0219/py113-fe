<template>
  <div>
    <section class="section">
      All Jokes
    </section>
    <section class="section">
      <b-button type="is-primary is-light" @click="search(1)">Get Jokes</b-button>
    </section>

    <section>
        <!-- Results -->
        <pre>
          {{ jokes }}
        </pre>
    </section>

  </div>
</template>

<script>
export default {
    data() {
      return {
        jokes: [],
      }
    },
    methods: {
      async search(page=1) {
        const response = await this.$axios.$get("https://hh-jokes-api.herokuapp.com/all-jokes")
        console.log(response)
        this.jokes = response
      },
    }
}
</script>
