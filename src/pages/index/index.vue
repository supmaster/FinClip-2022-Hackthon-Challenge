<template>
  <view class="index">
    <text>{{ msg }}</text>
    <button @tap="next">换一句</button>
  </view>
</template>

<script>
import { ref } from 'vue'
import './index.scss'
import Taro from '@tarojs/taro'

export default{
  setup () {
    const msg = ref('Hello world');
    return {
      msg
    }
  },
  methods:{
    async next(){
      console.log("Hello");
      const res = await Taro.request({
        url: 'https://v1.hitokoto.cn'
      })
      console.log(res);
      if(res.statusCode==200){
        this.msg = res.data.hitokoto;
      }else{
        this.msg = "你好";
      }
    }
  }
}
</script>
