<template>
  <h2>{{ status }}</h2>
  <button @click="random_coin">Toss a coin</button>
  <button @click="add_coin">Add coin</button>
  <button @click="remove_coin">Remove coin</button>
  <p>{{ status.length }}</p>
  <div class="container">
    <div class="coin" v-for="(coin, index) in status" :key="index">
      <p>{{ coin }}</p>
    </div>
  </div>
  <p>Head: {{ headLength }}</p>
  <p>Tail: {{ tailLength }}</p>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      status: ["H"],
      head: 0,
      tail: 0,
    };
  },
  methods: {
    random_coin() {
      const coin = "HT"
      
      this.status = this.status.map(x => {
        x = coin[Math.floor(Math.random() * 2)]
        return x
      } );

      // loop each item and change value
      // for (let i in this.status) {
      //   this.status[i] = coin[Math.floor(Math.random() * 2)]
      // }
    },
    add_coin() {
        this.status.push("H")
    },
    remove_coin() {
      this.status.pop()
    }
  },
  computed: {
    headLength() {
      // หาตัวใน array ที่ === H
      return this.status.filter(h => h === "H").length
    },
    tailLength() {
      // หาตัวใน array ที่ === T
      return this.status.filter(t => t === "T").length
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  text-align: center;
}

.container {
  display: flex;
  justify-content: center;
  text-align: center;
}

.coin {
  display: flex;
  justify-content: center;
  background-color: gold;
  border-radius: 50%;
  width: 5rem;
  height: 5rem;
  margin: 1rem;
  text-align: center;
}

.coin p {
  color: #fff;
  margin: 1rem;
  font-size: 2rem;
  align-self: center;
}


</style>
