<script setup>
import {ref} from 'vue'
import BaseTable from './components/Table/BaseTable.vue';
import TableRow from './components/Table/TableRow.vue';
import TableColumn from './components/Table/TableColumn.vue';

const tableHeads = ['Id', 'Author', 'Title', 'Cost', '']
const tableSizeColumns = '50px 1fr 2fr 150px 140px'

const books = ref([
  {
    id: 1,
    author: 'Dmitry Glukhovsky',
    title: 'Metro 2033',
    cost: 500,
  },
  {
    id: 12,
    author: 'James Clear',
    title: 'Atomic Habits: An Easy',
    cost: 600,
  },
  {
    id: 2,
    author: 'J. K. Rowling',
    title: 'Harry Potter and the Order of the Phoenix',
    cost: 1000,
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
        {{ book.author }}
      </TableColumn>
      <TableColumn>
        {{ book.title }}
      </TableColumn>
      <TableColumn>
        {{ book.cost }}
      </TableColumn>
    </TableRow>
  </BaseTable>
</template>
