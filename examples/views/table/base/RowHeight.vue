<template>
  <div>
    <p class="tip">修改行高，可以通过 <table-api-link prop="show-overflow"/> 和 <table-api-link prop="row-config"/>.height 修改行的高度</p>

    <vxe-table
      border
      resizable
      show-overflow
      height="500"
      :row-config="{height: 120}"
      :data="demo1.tableData">
      <vxe-column type="seq" title="序号" width="100"></vxe-column>
      <vxe-column title="图片" width="140" align="center">
        <template #default>
          <img src="/vxe-table/static/other/img1.gif" style="width: 100px;">
        </template>
      </vxe-column>
      <vxe-column title="基本信息">
        <template #default="{ row }">
          <div class="label-ellipsis">{{ row.name }}</div>
          <div class="label-ellipsis">{{ row.age }}</div>
          <div class="label-ellipsis">{{ row.address }}</div>
        </template>
      </vxe-column>
      <vxe-column field="age" title="Age" width="200"></vxe-column>
      <vxe-column field="address" title="Address" width="200"></vxe-column>
    </vxe-table>

    <p class="demo-code">{{ $t('app.body.button.showCode') }}</p>

    <pre>
      <pre-code class="xml">{{ demoCodes[0] }}</pre-code>
      <pre-code class="javascript">{{ demoCodes[1] }}</pre-code>
      <pre-code class="css">{{ demoCodes[1] }}</pre-code>
    </pre>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'

export default defineComponent({
  setup () {
    const demo1 = reactive({
      tableData: [
        { id: 10001, name: 'Test1', role: 'Develop', sex: 'Man', age: 28, address: 'vxe-table 从入门到放弃' },
        { id: 10002, name: 'Test2', role: 'Test', sex: 'Women', age: 22, address: 'Guangzhou' },
        { id: 10003, name: 'Test3', role: 'PM', sex: 'Man', age: 32, address: 'Shanghai' },
        { id: 10004, name: 'Test4', role: 'Designer', sex: 'Women', age: 23, address: 'vxe-table 从入门到放弃' },
        { id: 10005, name: 'Test5', role: 'Develop', sex: 'Women', age: 30, address: 'Shanghai' },
        { id: 10006, name: 'Test6', role: 'Designer', sex: 'Women', age: 21, address: 'vxe-table 从入门到放弃' },
        { id: 10007, name: 'Test7', role: 'Test', sex: 'Man', age: 29, address: 'vxe-table 从入门到放弃' },
        { id: 10008, name: 'Test8', role: 'Develop', sex: 'Man', age: 35, address: 'vxe-table 从入门到放弃' }
      ]
    })

    return {
      demo1,
      demoCodes: [
        `
        <vxe-table
          border
          resizable
          show-overflow
          height="500"
          :row-config="{height: 120}"
          :data="demo1.tableData">
          <vxe-column type="seq" title="序号" width="100"></vxe-column>
          <vxe-column title="图片" width="140" align="center">
            <template #default>
              <img src="/vxe-table/static/other/img1.gif" style="width: 100px;">
            </template>
          </vxe-column>
          <vxe-column title="基本信息">
            <template #default="{ row }">
              <div class="label-ellipsis">{{ row.name }}</div>
              <div class="label-ellipsis">{{ row.age }}</div>
              <div class="label-ellipsis">{{ row.address }}</div>
            </template>
          </vxe-column>
          <vxe-column field="age" title="Age" width="200"></vxe-column>
          <vxe-column field="address" title="Address" width="200"></vxe-column>
        </vxe-table>
        `,
        `
        import { defineComponent, reactive } from 'vue'

        export default defineComponent({
          setup () {
            const demo1 = reactive({
              tableData: [
                { id: 10001, name: 'Test1', role: 'Develop', sex: 'Man', age: 28, address: 'vxe-table 从入门到放弃' },
                { id: 10002, name: 'Test2', role: 'Test', sex: 'Women', age: 22, address: 'Guangzhou' },
                { id: 10003, name: 'Test3', role: 'PM', sex: 'Man', age: 32, address: 'Shanghai' },
                { id: 10004, name: 'Test4', role: 'Designer', sex: 'Women', age: 23, address: 'vxe-table 从入门到放弃' },
                { id: 10005, name: 'Test5', role: 'Develop', sex: 'Women', age: 30, address: 'Shanghai' },
                { id: 10006, name: 'Test6', role: 'Designer', sex: 'Women', age: 21, address: 'vxe-table 从入门到放弃' },
                { id: 10007, name: 'Test7', role: 'Test', sex: 'Man', age: 29, address: 'vxe-table 从入门到放弃' },
                { id: 10008, name: 'Test8', role: 'Develop', sex: 'Man', age: 35, address: 'vxe-table 从入门到放弃' }
              ]
            })

            return {
              demo1
            }
          }
        })
        `,
        `
        .label-ellipsis {
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
        `
      ]
    }
  }
})
</script>

<style lang="scss" scoped>
.label-ellipsis {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
