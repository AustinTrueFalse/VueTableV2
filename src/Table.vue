<script setup>
import {ref} from 'vue'
import BaseTable from './components/Table/BaseTable.vue';
import TableRow from './components/Table/TableRow.vue';
import TableColumn from './components/Table/TableColumn.vue';

const tableHeads = ['Id', 'Action', 'Descr', 'Summa', '']
const tableSizeColumns = '100px 1fr 2fr 150px 140px'

const books = ref([
  {
    id: 12345678,
    action: '30 % Помидоры',
    descr: 'Баллы за покупку',
    summa: 500,
  },
  {
    id: 12345679,
    action: '50% Хлеб',
    descr: 'Баллы за категорию в чеке',
    summa: 600,
  },
  {
    id: 12345690,
    action: '50% Огурцы',
    descr: 'Баллы за визит',
    summa: 1000,
  }
])


</script>



<template>
  <h1 class="heading-1">Table</h1>
  <BaseTable
    :head="tableHeads"
    :columnTemplates="tableSizeColumns">
    <TableRow
    v-for="book in books"
    :key="book.id"
    :columnTemplates="tableSizeColumns"
    >
      <TableColumn>
        {{ book.id }}
      </TableColumn>
      <TableColumn>
        {{ book.action }}
      </TableColumn>
      <TableColumn>
        {{ book.descr }}
      </TableColumn>
      <TableColumn>
        {{ book.summa }}
      </TableColumn>
    </TableRow>
  </BaseTable>
</template>
