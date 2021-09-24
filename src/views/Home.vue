<template>
  <div class="home">
    <button @click="add()" :class="showEdit.editvalue ? 'redBg' : 'redColor'" >
      点我点我{{ aaa.title }}
    </button>
  </div>
</template>

<script>
import { reactive, watch } from "vue";
export default {
  name: "Home",
  components: {},
  props: {
    title: Number,
  },
  setup(props, context) {
    console.log(props);
    let showEdit = reactive({editvalue:false,isis:false});
    const aaa = reactive(props);
    // add(()=>{
    //   console.log(context,"abc")
    // })
    function add() {
      context.emit("showdown");
      
      // watch(aaa.title,(newValue,oldValue)=>{
      //   console.log(newValue,oldValue)
      // })
    }
    watch(
      () => aaa.title,
      (newValue, oldValue) => {
        if (newValue > 110) {
          showEdit.editvalue = true;
          showEdit.isis = true
        }
        console.log(newValue, oldValue, showEdit, "sjow");
      }
    );
    return {
      aaa,
      add,
      showEdit,
    };
  },
};
</script>
<style scoped>
.redBg {
  background: red;
}
</style>
