<script setup>
import {ref, computed} from 'vue'
import BaseTable from './components/Table/BaseTable.vue';
import TableRow from './components/Table/TableRow.vue';
import TableColumn from './components/Table/TableColumn.vue';

const tableHeads = ['Id', 'Action', 'Descr', 'Summa', '']
const cardHeads = ['Discount Card', 'LastUpdate', 'Status']
const tableSizeColumns = '120px 1fr 2fr 150px 140px'

const rows = ref([
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

const cards = ref([
  {
      discountCard: 47009636604,
      lastUpdate: '30.03.2021',
      isActive: false,
      status: '',
    },
    {
      discountCard: 802507125933,
      lastUpdate: '30.03.2021',
      isActive: true,
      status: '',
    },
])


const testActive = computed(() => {
  return cards.isActive ? 'Активна' : 'Неактивна'
})


</script>



<template>
    <div class="body">
      <h1 class="heading-1">Table</h1>
      <div class="main__info"></div>
        <div class="main__cards">
          <BaseTable
            :head="cardHeads"
            :columnTemplates="tableSizeColumns">
            <TableRow
            v-for="card in cards"
            :key="card.discountCard"
            :columnTemplates="tableSizeColumns"
            >
              <TableColumn>
                {{ card.discountCard }}  
              </TableColumn>

              <TableColumn>
                {{ card.lastUpdate }}
              </TableColumn>

              <TableColumn
              class="status__field"
              :class="{ 'deactive': !card.isActive }"
              >
                {{ testActive }}
              </TableColumn>

              <!-- <TableColumn
              class="status__field"
              :class="{ 'deactive': !card.isActive }"
              v-if="card.isActive"
              >
                {{ 'Активна' }}
              </TableColumn>

              <TableColumn
              class="status__field"
              :class="{ 'deactive': !card.isActive }"
              v-else="card.isActive"
              >
                {{ 'Заблокирована' }}
              </TableColumn> -->

            </TableRow>
          </BaseTable>
        </div>
        <div class="main__data">
          <BaseTable
            :head="tableHeads"
            :columnTemplates="tableSizeColumns">
            <TableRow
            v-for="row in rows"
            :key="row.id"
            :columnTemplates="tableSizeColumns"
            >
              <TableColumn>
                {{ row.id }}  
              </TableColumn>
              <TableColumn>
                {{ row.action }}
              </TableColumn>
              <TableColumn>
                {{ row.descr }}
              </TableColumn>
              <TableColumn>
                {{ row.summa }}
              </TableColumn>
            </TableRow>
          </BaseTable>
        </div>
    </div>
</template>


<style>

@import url('https://fonts.googleapis.com/css2?family=Kanit:wght@400;600&family=Montserrat&display=swap');

  * {
      box-sizing: border-box;
  }

  .body {
    margin: 0;
    font-family: 'Montserrat', sans-serif; 
  }

  .main__info {
    max-width: 1010px;
    color: #2c2c2c;;
  }

  .main__cards {
    background: rgb(216,219,248);
    background: linear-gradient(90deg, rgba(216,219,248,0.22172619047619047) 3%, rgba(227,229,246,1) 49%, rgba(245,245,245,1) 77%);
    padding: 10px;
    border-radius: 50px;
    max-width: 1010px;
    margin: 0 auto;
    margin-bottom: 50px;
    color: #2c2c2c;;
  }

  .main__data {
    background: rgb(216,219,248);
    background: linear-gradient(90deg, rgba(216,219,248,0.22172619047619047) 3%, rgba(227,229,246,1) 49%, rgba(245,245,245,1) 77%);
    padding: 10px;
    border-radius: 50px;
    max-width: 1010px;
    margin: 0 auto;
    margin-bottom: 50px;
    color: #2c2c2c;;
  }

  .status__field {
    color: rgb(9, 170, 17);
  }

  .status__field.deactive {
    color: rgb(196, 4, 4);
  }


  



  
</style>
