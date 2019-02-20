<template>
  <div class="todolist">
    <ul class="todolist-ul">
      <li v-for="(list, index) in todolists" :key="index">
        {{ todolists[index] }}
        <span class="delete-list-btn" @click="deleteOneList(index)"><img src="../assets/deletebtn.png" alt="delete"></span>
        <span class="edit-list-btn" @click="editOneList(index)"><img src="../assets/edit.png" alt="edit"></span>
        <!-- <input v-if="editList[index]" v-model="editListContent" class="edit-list-input" type="text" @blur="editListToLists()"> -->
      </li>
    </ul>
    <span v-if="!addList" class="add-list"><button @click="addOneList()">+</button></span>
    <input v-model="addListContent" class="add-list-input" v-if="addList" type="text" @blur="addListToLists()">
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component'
// import AddList from './AddList.vue'
@Component({
  // components: {
  //   'g-addList': AddList
  // }
})
export default class Todolist extends Vue {
  todolists: string[] = [
    'learn typescript',
    'learn vue',
    'learn english',
    'join meeting'
  ]
  addList: boolean = false
  editList: boolean[] = [false]
  addListContent: string = ''
  editListContent: string = ''
  addOneList () {
    this.addList = true
  }
  editListToLists (value: string) {
    // if (this.editListContent) {
    //   this.todolists
    //   this.addList = false
    //   this.addListContent = ''
    // }
  }
  addListToLists (value: string) {
    if (this.addListContent) {
      this.todolists.push(this.addListContent)
      this.addList = false
      this.addListContent = ''
    }
  }
  editOneList (index: number) {
    // this.editList[index] = true
    this.deleteOneList(index)
    this.addList = true
  }
  deleteOneList (index: number) {
    this.todolists.splice(index, 1)
  }
}
</script>

<style>
  ul.todolist-ul {
    width: 40%;
    margin: 0 auto;
    padding: 0;
  }
  ul.todolist-ul li {
    padding-right: 16px;
    height: 40px;
    line-height: 40px;
    border-bottom: 1px solid #0dbc79;
    list-style-type: none;
  }
  .delete-list-btn, .edit-list-btn {
    margin-left: 16px;
    float: right;
    color: red;
    font-size: 24px;
  }
  .delete-list-btn:hover, .edit-list-btn:hover {
    cursor: pointer;
  }
  .add-list {
    width: 40%;
    height: 40px;
    line-height: 40px;
    margin: 0 auto;
    border-bottom: 1px solid #0dbc79;
    display: block;
  }
  .add-list button {
    background-color: #fff;
    border: none;
    font-size: 32px;
    color: #0dbc79;
    outline: none;
  }
  .add-list-input {
    width: 40%;
    height: 40px;
    line-height: 40px;
    margin: 0 auto;
    border: 1px solid #0dbc79;
    text-indent: 16px;
    outline: none;
    display: block;
  }
  .edit-list-input {
    width: 100%;
    height: 40px;
    line-height: 40px;
    border: 1px solid #0dbc79;
    text-indent: 16px;
    outline: none;
    display: block;
  }
</style>
