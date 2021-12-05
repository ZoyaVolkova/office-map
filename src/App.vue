<template>
  <div id="app">
    <div class="office">
      <Map @click="getId" @update:isUserOpenned="isUserOpenned = $event" />
      <SideMenu
        :isUserOpenned="isUserOpenned"
        :person="person"
        @update:isUserOpenned="isUserOpenned = $event"
      />
    </div>
  </div>
</template>

<script>
import Map from './components/Map.vue'
import SideMenu from './components/SideMenu.vue'
import people from './assets/data/people.json'

export default {
  name: 'App',
  components: {
    Map,
    SideMenu,
  },
  data() {
    return {
      people: [],
      person: null,
      isUserOpenned: false,
    }
  },
  created() {
    this.people = people
  },
  methods: {
    getId(id) {
      const person = people.find((person) => {
        return id == person.tableId
      })

      if (person) {
        this.isUserOpenned = true
        this.person = person
      } else {
        this.isUserOpenned = false
        this.person = null
      }
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  background-color: #fafafa;
  padding: 24px;
  box-sizing: border-box;
}

html,
body,
#app {
  height: 100%;
}

* {
  box-sizing: border-box;
}

h3 {
  margin-top: 0px;
}

.office {
  display: grid;
  grid-template-columns: 1fr 320px;
  border-radius: 6px;
  border: 1px solid #ccd8e4;
  height: 100%;
  background: white;
  max-width: 1500px;
  margin: 0 auto;
}
</style>
