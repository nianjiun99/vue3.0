<template>
  <home :title="title" @showdown="showdown"></home>
  <!-- <ul>
    <li v-for="(item, index) in defaultData.tableData" :key="index">
      {{ item.name }}
    </li>
  </ul> -->
  <el-table :data="defaultData.tableData" border style="width: 100%">
    <el-table-column prop="date" label="日期" width="180"> </el-table-column>
    <el-table-column prop="name" label="姓名" width="180"> </el-table-column>
    <el-table-column prop="address" label="地址"> </el-table-column>
  </el-table>
</template>

<script>
import { reactive, onMounted, ref,  } from "vue";
import home from "./Home.vue";
export default {
  components: {
    home,
  },
  setup() {
    //reactive 定义对象    ref 定义常量

    const title = ref(100);
    const defaultData = reactive({
      tableData: [
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
      ],
    });
    function showdown() {
      const objValue = {
        date: title.value,
        name: `校长${title.value}`,
        address: `上海市普陀区金沙江路 ${title.value} 弄`,
      };
      title.value++;
      defaultData.tableData.push(objValue);
    }
    onMounted(() => {
      defaultData.tableData[0].name = "张三";
      console.log(defaultData.tableData, "75456");
    });

    // watch(title, (newValue, oldValue) => {
    //   console.log(newValue, oldValue, "76565465");
    // });
    return { defaultData, showdown, title };
  },
};
</script>
