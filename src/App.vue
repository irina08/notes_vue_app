<template>
  <div id="app">
    <h1 class="ui centered header">Vue.js Notes App</h1>
    <div class='ui one column centered grid'>
      <div class='column'>
        <list-notes v-bind:notes="notes"></list-notes>
        <create-note v-on:create-note="createNote"></create-note>
      </div>
    </div>
  </div>
</template>

<script>
  import ListNotes from './components/ListNotes';
  import CreateNote from './components/CreateNotes';
  export default {
    name: 'app',
    components: {
      ListNotes,
      CreateNote
    },
    data() {
      return {
        notes: [{
          title: 'Vue homework',
          description: 'Before read materials about Vue.'
        }, {
          title: 'Gym',
          description: 'Do not be late. It will close at 8 pm.'
        }, {
          title: 'Call Helen',
          description: 'Ask her about car show in San Francisco?'
        }],
      }
    },
    methods: {
      createNote(note) {
        this.notes.push(note);
        //alert('Note created!');
      }
    }
  };
</script>

<style>
html {
    position: relative;
}
#app {
  background-color: aquamarine;
  padding-top: 45px;
  width: 100%;
  margin: 0 auto;
}
@media (min-width: 600px) {
  #app { 
    width: 75%;
  }
}

</style>
