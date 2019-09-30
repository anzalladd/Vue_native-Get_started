<template>
  <view class="container">
    <text class="text-color-primary">TODO APP</text>
    <text-input type="text" class="my-input" v-model="item" placeholder="Input your todo"/>
    <view class="btn-group">
      <touchable-opacity :on-press="submitData">
        <text class="my-btn">Submit</text>
      </touchable-opacity>
      <touchable-opacity :on-press="resetData">
        <text class="my-btn-danger">Reset</text>
      </touchable-opacity>
    </view>
    <view>
    <view class="list-wrapper" v-if="data.length == 0">
      <text class="empty">Your TODO is empty</text>
    </view>
    <view class="list-wrapper" v-else>
      <text v-for="(item, index) in data" :key="index" class="empty">{{`${index+1}. ${item}` }}</text>
    </view>
  </view>
</template>

<script>
import React from 'react'
import { Text } from 'react-native'
export default {
  name: 'myApp',
  data: () => ({
    item: '',
    data: []
  }),
  methods: {
    submitData() {
      if(this.item.length > 0){
        this.data.push(this.item)
        this.item = ''
      }
      else{
        alert('Please fill the input')
      }
    },
    resetData() {
      this.data = []
    },
  }
}
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
  padding-left: 20px;
  padding-right: 20px;
}
.text-color-primary {
  color: #6200EE;
  font-size: 25px;
  font-weight: bold;
}
.my-name{
  margin-top: 20px;
}
.my-input{
  width: 100%;
  border-width: 1px;
  padding-left: 20px;
  margin-top: 20px;
  margin-bottom: 20px;
}
.my-btn{
  background-color: #6200EE;
  color: white;
  padding-vertical: 10px;
  padding-horizontal: 30px;
  border-radius: 5px;
  margin-horizontal: 5px;
}
.my-btn-danger{
  background-color:#F34F43;
  color: white;
  padding-vertical: 10px;
  padding-horizontal: 30px;
  border-radius: 5px;
  margin-horizontal: 5px;
}
.btn-group{
  flex-direction: row; 
}
.list-wrapper{
  margin-top: 20px;
}
.empty{
  font-weight: bold;
  font-size: 16px;
}
</style>
