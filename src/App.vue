<template>
  
  <div class="container grid-lg my-2 py2 text-dark">

    <div class="card">

      <div class="card-header">
        <div class="h4"> Exibindo as Moedas </div>
      </div>
     
      <div class="card-body">

        <HelloWorld :quotes="quotes" />


      </div>



    </div>

  </div>

</template>

<script>

  import { onMounted, reactive, toRefs  } from 'vue';
  import api from '@/servidor/api.js';
  import HelloWorld from './components/HelloWorld.vue';

  export default {

    name: 'App',

    components: { HelloWorld },

    // expondo as nossas variaveis para o template
    setup() {

      const data = reactive ({  // raactive são dados reativos
        quotes: { }, // quotes são as cotações
      });

      onMounted( async() => {

        const response = await api.all();
        data.quotes = response.data;

      })

      return { ...toRefs(data) 
      }
    }


  }
</script>



<style scoped>
    .card{
 
      box-shadow: inset 0 0 1em gold, 0 0 1em red;   

    }

    .h4 {
      text-align: center;
      margin-bottom: 10px;
    }
</style>


