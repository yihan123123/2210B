<template>
  名称：{{ name }} 数量：{{ num }} 价格：{{ price }} 总价：{{ res }}
  <button @click="addn">加数量</button>
  <button @click="addp">加价格</button>
  <div>user修改</div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import { toRefs, reactive, ref,watchEffect,watch} from 'vue'
export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  setup(props, ctx) {
    let obj = reactive({
      name: '冰墩墩',
      num: 1,
      price: 10
    })
    let addn=()=>{
      obj.num++
    }
    let addp=()=>{
      obj.price++
    }
    let res=ref(0)
    watchEffect(()=>{
      res.value=obj.price*obj.num
    })
    watch()
    watchEffect(()=>{})
    return {
      ...toRefs(obj),
      addn,
      addp,
      res,
    }
  }
}
</script>
