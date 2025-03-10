<template>
  <div>
    <p class="tip">
      当一个表格高度需要自适应的时候可以通过 <table-api-link prop="max-height"/> 设置为最大高度
    </p>

    <vxe-toolbar>
      <template #buttons>
        <vxe-button @click="$refs.xTree.setAllTreeExpand(true)">展开所有</vxe-button>
        <vxe-button @click="$refs.xTree.clearTreeExpand()">关闭所有</vxe-button>
      </template>
    </vxe-toolbar>

    <vxe-table
      border
      resizable
      ref="xTree"
      max-height="400"
      :tree-config="{transform: true, rowKey: 'id', parentKey: 'parentId'}"
      :data="tableData">
      <vxe-column field="name" title="app.body.label.name" tree-node></vxe-column>
      <vxe-column field="size" title="Size"></vxe-column>
      <vxe-column field="type" title="Type"></vxe-column>
      <vxe-column field="date" title="Date"></vxe-column>
    </vxe-table>

    <p class="demo-code">{{ $t('app.body.button.showCode') }}</p>

    <pre>
      <pre-code class="xml">{{ demoCodes[0] }}</pre-code>
      <pre-code class="typescript">{{ demoCodes[1] }}</pre-code>
    </pre>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup () {
    const tableData = ref([
      { id: 10000, parentId: null, name: 'vxe-table 从入门到放弃1', type: 'mp3', size: 1024, date: '2020-08-01' },
      { id: 10050, parentId: null, name: 'Test2', type: 'mp4', size: null, date: '2021-04-01' },
      { id: 24300, parentId: 10050, name: 'Test3', type: 'avi', size: 1024, date: '2020-03-01' },
      { id: 20045, parentId: 24300, name: 'vxe-table 从入门到放弃4', type: 'html', size: 600, date: '2021-04-01' },
      { id: 10053, parentId: 24300, name: 'vxe-table 从入门到放弃96', type: 'avi', size: null, date: '2021-04-01' },
      { id: 24330, parentId: 10053, name: 'vxe-table 从入门到放弃5', type: 'txt', size: 25, date: '2021-10-01' },
      { id: 21011, parentId: 10053, name: 'Test6', type: 'pdf', size: 512, date: '2020-01-01' },
      { id: 22200, parentId: 10053, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 23666, parentId: null, name: 'Test8', type: 'xlsx', size: 2048, date: '2020-11-01' },
      { id: 23677, parentId: 23666, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 23671, parentId: 23677, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 23672, parentId: 23677, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 23688, parentId: 23666, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 23681, parentId: 23688, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 23682, parentId: 23688, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 24555, parentId: null, name: 'vxe-table 从入门到放弃9', type: 'avi', size: 224, date: '2020-10-01' },
      { id: 24566, parentId: 24555, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
      { id: 24577, parentId: 24555, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' }
    ])
    return {
      tableData,
      demoCodes: [
        `
        <vxe-toolbar>
          <template #buttons>
            <vxe-button @click="$refs.xTree.setAllTreeExpand(true)">展开所有</vxe-button>
            <vxe-button @click="$refs.xTree.clearTreeExpand()">关闭所有</vxe-button>
          </template>
        </vxe-toolbar>

        <vxe-table
          border
          resizable
          ref="xTree"
          max-height="400"
          :tree-config="{transform: true, rowKey: 'id', parentKey: 'parentId'}"
          :data="tableData">
          <vxe-column field="name" title="app.body.label.name" tree-node></vxe-column>
          <vxe-column field="size" title="Size"></vxe-column>
          <vxe-column field="type" title="Type"></vxe-column>
          <vxe-column field="date" title="Date"></vxe-column>
        </vxe-table>
        `,
        `
        import { defineComponent, ref } from 'vue'

        export default defineComponent({
          setup () {
            const tableData = ref([
              { id: 10000, parentId: null, name: 'vxe-table 从入门到放弃1', type: 'mp3', size: 1024, date: '2020-08-01' },
              { id: 10050, parentId: null, name: 'Test2', type: 'mp4', size: null, date: '2021-04-01' },
              { id: 24300, parentId: 10050, name: 'Test3', type: 'avi', size: 1024, date: '2020-03-01' },
              { id: 20045, parentId: 24300, name: 'vxe-table 从入门到放弃4', type: 'html', size: 600, date: '2021-04-01' },
              { id: 10053, parentId: 24300, name: 'vxe-table 从入门到放弃96', type: 'avi', size: null, date: '2021-04-01' },
              { id: 24330, parentId: 10053, name: 'vxe-table 从入门到放弃5', type: 'txt', size: 25, date: '2021-10-01' },
              { id: 21011, parentId: 10053, name: 'Test6', type: 'pdf', size: 512, date: '2020-01-01' },
              { id: 22200, parentId: 10053, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 23666, parentId: null, name: 'Test8', type: 'xlsx', size: 2048, date: '2020-11-01' },
              { id: 23677, parentId: 23666, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 23671, parentId: 23677, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 23672, parentId: 23677, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 23688, parentId: 23666, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 23681, parentId: 23688, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 23682, parentId: 23688, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 24555, parentId: null, name: 'vxe-table 从入门到放弃9', type: 'avi', size: 224, date: '2020-10-01' },
              { id: 24566, parentId: 24555, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' },
              { id: 24577, parentId: 24555, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' }
            ])
            return {
              tableData
            }
          }
        })
        `
      ]
    }
  }
})
</script>
