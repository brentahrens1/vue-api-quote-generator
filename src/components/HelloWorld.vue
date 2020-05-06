<template>
  <div class="hello">
    <p>{{ results.quote }}</p>
    <h1>{{ results.author }}</h1>
    <button @click="handleClick">New Quote</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      results: []
    }
  },
  mounted() {
    this.getQuote()
  },
  methods: {
    getQuote() {
      let url = 'https://gist.githubusercontent.com/camperbot/5a022b72e96c4c9585c32bf6a75f62d9/raw/e3c6895ce42069f0ee7e991229064f167fe8ccdc/quotes.json'
      fetch(url)
      .then(res => res.json())
      .then(data => {
        let dataQuote = data.quotes
        let randomQuote = Math.floor(Math.random() * dataQuote.length)
        this.results = dataQuote[randomQuote]
      })
    },
    handleClick() {
      this.getQuote()
  }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
