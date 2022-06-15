<template>
  <h1>Counter - Vuex</h1>
  <h2>Direct access: {{$store.state.count}} </h2>
  <!-- <h2>Computed: {{countComputed}}</h2> -->

  <h1>mapState</h1>
  <h2>mapState: {{count}}</h2>
  <h2>lastMutation: {{lastMutation}}</h2>

  <button @click="increment">+1</button>
  <button @click="incrementBy">+5</button>
  <button @click="randomInt">Random</button>
</template>

<script>
import { mapState, mapActions } from "vuex";

export default {
    // computed: mapState(['count'])
    computed: {
        countComputed(){
            return this.$store.state.count
        },
        ...mapState(['count', 'lastMutation'])
        // ...mapState({
        //     count: state => state.count,
        //     // lastMutation: state => state.lastMutation,
        //     lastMutation: 'lastMutation'
        // })
    },
    methods: {
        increment(){
            this.$store.commit('increment')
        },
        incrementBy(){
            this.$store.commit('incrementBy', 5)
        },
        // incrementRandomInt(){
        //     this.$store.dispatch('incrementRandomInt')
        // }
        // ...mapActions(['incrementRandomInt'])
        ...mapActions({
            randomInt: 'incrementRandomInt'
        })
    }
}
</script>
