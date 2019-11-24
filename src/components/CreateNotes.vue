<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card ww' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text'>
          </div>
          <div class='field'>
            <label>Description</label>
            <input v-model="descriptionText" type='text'>
          </div>
          <div class='ui two buttons'>
            <button class='ui basic green button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      titleText: '',
      descriptionText: '',
      isCreating: false
    };
  },
  methods: {
    openForm () {
      this.isCreating = true;
    },
    closeForm () {
      this.isCreating = false;
    },
    sendForm () {
      if (this.titleText.length > 0 && this.descriptionText.length > 0) {
        const title = this.titleText;
        const description = this.descriptionText;
        this.$emit('create-note', {
          title,
          description,
        });
        // Clean fields after submit
        this.titleText = '';
        this.descriptionText = '';
        this.isCreating = false;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@media (min-width: 768px) {
  div.ww {
      width: 75%;
  }
}
</style>
