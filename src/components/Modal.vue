<template>
    <div>
      <div class="md-modal modal-msg md-modal-transition" v-bind:class="{'md-show':mdShow}">
        <div class="md-modal-inner">
          <div class="md-top">
            <button class="md-close" @click="closeModal">关闭</button>
          </div>
          <div class="md-content">
            <div class="confirm-tips">
              <!--定义插槽，要起名字，不起名字时默认只有一个插槽-->
              <slot name="message"></slot>
            </div>
            <div class="btn-wrap">
              <slot name="btnGroup"></slot>
            </div>
          </div>
        </div>
      </div>
      <div class="md-overlay" v-if="mdShow" @click="closeModal"></div>
    </div>
</template>
<script>
    export default{
        name:'modal',
        props:['mdShow'],
        methods:{
          closeModal(){
            //父子组件传递必须用$emit触发一个事件，这里即close事件
            this.$emit('close');
          }
        }
    }
</script>
