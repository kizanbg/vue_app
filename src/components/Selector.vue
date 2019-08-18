<template>
  <div>
    <div class="info-box">{{message}}</div>
    <select
            v-if="selected !== '10+'"
            @change="onchange()"
            v-model="selected">
      <option
              v-for="option in options"
              :value="option"
              :key="option" > {{ option }} </option>
    </select>
    <div v-else>
      <input type="number" name="inputfield" v-model="inputfield" value=""/><button @click="updateInput()">Update</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Selector',
    data() {
      return {
        message: 'Select the quantity of the product',
        options: [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, '10+' ],
        selected: -1,
        inputfield: 11
      };
    },
    methods: {
      onchange() {
        if(this.selected == '10+'){
          this.message = 'Enter the quantity of the product';
        } else {
          this.message= "You have selected "+this.selected+" products";
        }
      },
      updateInput() {
        this.message = 'You have entered '+this.inputfield+' products';
      }
    }
  };
</script>

<style scoped>

</style>
