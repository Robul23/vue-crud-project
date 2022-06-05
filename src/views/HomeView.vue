<template>
  <div class="home">
     <h1>Movie tracker web app</h1>
    <DataTable/>
  </div>
</template>

<script>
// @ is an alias to /src
import DataTable from '@/components/DataTable.vue'

export default {
  name: 'HomeView',
  components: {
    DataTable
    
}
}
</script>
