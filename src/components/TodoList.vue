<template>
  <div class="todolist">
    <ul class="todolist-ul">
      <li v-for="(list, index) in todolists" :key="index">
        <input class="edit-list-input" v-model="todolists[index]">
        <span class="edit-list-btn" @click="editOneList(index)"><img src="../assets/edit.png" alt="edit"></span>
        <span class="delete-list-btn" @click="deleteOneList(index)"><img src="../assets/deletebtn.png" alt="delete"></span>
      </li>
    </ul>
    <span v-show="!addList" class="add-list"><button @click="addOneList()">+</button></span>
    <input v-model="addListContent" class="add-list-input" v-show="addList" type="text" @blur="addListToLists()">
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Component, Watch } from 'vue-property-decorator'
@Component
export default class Todolist extends Vue {
  todolists: string[] = [
    'aaa'
  ]
  addList: boolean = false
  addListContent: string = ''
  editOneList (index: number, el: any) {
    document.getElementsByTagName('input')[index].focus()
  }
  addOneList () {
    this.addList = true
  }
  addListToLists (value: string) {
    if (this.addListContent) {
      this.todolists.push(this.addListContent)
      this.addList = false
      this.addListContent = ''
    } else {
      this.addList = false
    }
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
    position: relative;
    height: 40px;
    line-height: 40px;
    text-align: left;
    border-bottom: 1px solid #0dbc79;
    list-style-type: none;
  }
  .delete-list-btn, .edit-list-btn {
    margin-left: 16px;
    color: red;
    font-size: 24px;
    position: absolute;
  }
  .edit-list-btn {
    right: 40px;
  }
  .delete-list-btn {
    right: 0;
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
    font-size: 20px;
    margin: 10px auto 0;
    border: 1px solid #0dbc79;
    border-radius: 5px;
    text-indent: 16px;
    outline: none;
    display: block;
  }
  .edit-list-input {
    width: calc(100% - 80px);
    font-size: 20px;
    border: none;
    outline: none;
    text-indent: 16px;
  }
  .edit-list-input:focus {
    height: 38px;
    border-radius: 5px;
    border: 1px solid #0dbc79;
  }
</style>
