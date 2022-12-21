<template>
    <div class="context" v-if="isShow" :style="styles">
    <div
         class="context__item"
         v-for="(item, idx) in items"
    :key="idx"
    @click="onClick(item)"
       >
    {{ item.text }}
    </div>
    </div>
   </template>
   
   <script>
   export  {
    name: "Contextmenu",
     data() {
       return {
    isShow: false,
    items: [],
    xPos: 0,
    yPos: 0,
       };
     },
    mounted() {
       this.$context.EventBus.$on("show", this.onShown);
       this.$context.EventBus.$on("close", this.onClose);
     },
     beforeDestroy() {
       this.$context.EventBus.$off("show", this.onShown);
       this.$context.EventBus.$off("close", this.onClose);
     },
   };
   </script>
   
   <style lang="scss" scoped>
   .context {
     position: absolute;
     background: #eee;
     cursor: pointer;
   }
   </style>