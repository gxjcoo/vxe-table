<template>
  <div>
    <p class="tip">
      树表格与展开行同时使用，非常简单就能实现很复杂的树形展开行
    </p>

    <vxe-table
      border
      resizable
      :tree-config="{children: 'children'}"
      :data="tableData">
      <vxe-column field="name" title="Name" tree-node></vxe-column>
      <vxe-column type="expand" title="Details" width="80">
        <template #content="{ row }">
          <ul class="expand-wrapper">
            <li>
              <span>ID：</span>
              <span>{{ row.id }}</span>
            </li>
            <li>
              <span>Name：</span>
              <span>{{ row.name }}</span>
            </li>
            <li>
              <span>Date</span>
              <span>{{ row.date }}</span>
            </li>
          </ul>
        </template>
      </vxe-column>
      <vxe-column field="size" title="Size"></vxe-column>
      <vxe-column field="type" title="Type"></vxe-column>
      <vxe-column field="date" title="Date"></vxe-column>
    </vxe-table>

    <p class="demo-code">{{ $t('app.body.button.showCode') }}</p>

    <pre>
      <pre-code class="xml">{{ demoCodes[0] }}</pre-code>
      <pre-code class="typescript">{{ demoCodes[1] }}</pre-code>
      <pre-code class="css">{{ demoCodes[2] }}</pre-code>
    </pre>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup () {
    const tableData = ref([
      { id: 1000, name: 'vxe-table 从入门到放弃1', type: 'mp3', size: 1024, date: '2020-08-01' },
      {
        id: 1005,
        name: 'Test2',
        type: 'mp4',
        size: null,
        date: '2021-04-01',
        children: [
          { id: 24300, name: 'Test3', type: 'avi', size: 1024, date: '2020-03-01' },
          { id: 20045, name: 'vxe-table 从入门到放弃4', type: 'html', size: 600, date: '2021-04-01' },
          {
            id: 10053,
            name: 'vxe-table 从入门到放弃96',
            type: 'avi',
            size: null,
            date: '2021-04-01',
            children: [
              { id: 24330, name: 'vxe-table 从入门到放弃5', type: 'txt', size: 25, date: '2021-10-01' },
              { id: 21011, name: 'Test6', type: 'pdf', size: 512, date: '2020-01-01' },
              { id: 22200, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' }
            ]
          }
        ]
      },
      { id: 23666, name: 'Test8', type: 'xlsx', size: 2048, date: '2020-11-01' },
      { id: 24555, name: 'vxe-table 从入门到放弃9', type: 'avi', size: 224, date: '2020-10-01' }
    ])
    return {
      tableData,
      demoCodes: [
        `
        <vxe-table
          border
          resizable
          :tree-config="{children: 'children'}"
          :data="tableData">
          <vxe-column field="name" title="Name" tree-node></vxe-column>
          <vxe-column type="expand" title="Details" width="80">
            <template #content="{ row }">
              <ul class="expand-wrapper">
                <li>
                  <span>ID：</span>
                  <span>{{ row.id }}</span>
                </li>
                <li>
                  <span>Name：</span>
                  <span>{{ row.name }}</span>
                </li>
                <li>
                  <span>Date</span>
                  <span>{{ row.date }}</span>
                </li>
              </ul>
            </template>
          </vxe-column>
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
              { id: 1000, name: 'vxe-table 从入门到放弃1', type: 'mp3', size: 1024, date: '2020-08-01' },
              {
                id: 1005,
                name: 'Test2',
                type: 'mp4',
                size: null,
                date: '2021-04-01',
                children: [
                  { id: 24300, name: 'Test3', type: 'avi', size: 1024, date: '2020-03-01' },
                  { id: 20045, name: 'vxe-table 从入门到放弃4', type: 'html', size: 600, date: '2021-04-01' },
                  {
                    id: 10053,
                    name: 'vxe-table 从入门到放弃96',
                    type: 'avi',
                    size: null,
                    date: '2021-04-01',
                    children: [
                      { id: 24330, name: 'vxe-table 从入门到放弃5', type: 'txt', size: 25, date: '2021-10-01' },
                      { id: 21011, name: 'Test6', type: 'pdf', size: 512, date: '2020-01-01' },
                      { id: 22200, name: 'Test7', type: 'js', size: 1024, date: '2021-06-01' }
                    ]
                  }
                ]
              },
              { id: 23666, name: 'Test8', type: 'xlsx', size: 2048, date: '2020-11-01' },
              { id: 24555, name: 'vxe-table 从入门到放弃9', type: 'avi', size: 224, date: '2020-10-01' }
            ])
            return {
              tableData
            }
          }
        })
        `,
        `
        .expand-wrapper {
          padding: 20px;
        }
        `
      ]
    }
  }
})
</script>

<style lang="scss" scoped>
.expand-wrapper {
  padding: 20px;
}
</style>
