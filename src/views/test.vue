<template>
  <div>
    <pdf-component></pdf-component>
    <el-button @click="loadExcel()">下载excel文件</el-button>
  </div>
</template>

<script>
import pdfComponent from '@/components/pdfComponent.vue'
import { toExcel } from '@/assets/js/file'
export default {
  components: {
    pdfComponent
  },
  data () {
    return {
      excelData: [
        {
          name: '张三',
          birthday: new Date('1990-01-01'),
          sex: '男',
          age: 28
        },
        {
          name: '李四',
          birthday: new Date('1991-01-01'),
          sex: '女',
          age: 27
        }
      ]
    }
  },
  methods: {
    loadExcel () {
      const th = ['姓名', '生日', '性别', '年龄']
      const filterVal = ['name', 'birthday', 'sex', 'age']
      const data = this.excelData.map(v => filterVal.map(k => v[k]))
      const [fileName, fileType, sheetName] = ['测试下载', 'xlsx', '测试页']
      console.log(th, data, fileName, fileType, sheetName)
      toExcel({th, data, fileName, fileType, sheetName})
    }
  }
}
</script>
