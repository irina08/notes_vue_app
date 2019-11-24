<template>
  <div>
    <note v-on:delete-note="deleteNote" v-for="note in notes" :note.sync="note"></note>
  </div>
</template>

<script>
  import Note from './Note';
  export default {
    props: ['notes'],
    components: {
      Note
    },
    methods: {
      deleteNote(note) {
        var removeIt = confirm('Do you really want to remove it?');
        if (removeIt) {
          const noteIndex = this.notes.indexOf(note);
          this.notes.splice(noteIndex, 1);
          //alert('Note deleted!');
        }
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>