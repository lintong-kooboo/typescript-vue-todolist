<template>
  <div class="add-list-component">
    <span v-show="!addList" class="add-list"><button @click="addOneList()">+</button></span>
    <input v-model="addListContent" class="add-list-input" v-show="addList" type="text" @blur="addListToLists()">
  </div>
</template>

<script lang="ts">
// import Vue from 'vue'
import { Vue, Prop } from 'vue-property-decorator'
export default class AddList extends Vue {
  @Prop(String) todoLists: string[]
  @Prop(Boolean) addList: boolean
  addListContent: string = ''
  // methods = {
  //   addOneList () {
  //     this.addList = true
  //   }
  //   addListToLists (value: string) {
  //     if (this.addListContent) {
  //       this.todoLists.push(this.addListContent)
  //       this.addList = false
  //       this.addListContent = ''
  //     }
  //   }
  // }
  addOneList () {
    this.addList = true
  }
  addListToLists (value: string) {
    if (this.addListContent) {
      this.todoLists.push(this.addListContent)
      this.addList = false
      this.addListContent = ''
    }
  }
}
</script>
