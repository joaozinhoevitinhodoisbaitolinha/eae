<template>
  <div>
      <v-dialog
      v-model="dialog"
      persistent
      max-width="290"
    >
      <v-card>
        <v-card-title class="text-h5">
          Excluir
        </v-card-title>
        <v-divider></v-divider>
        <v-card-text
        class="mt-2"
        >Tem certeza que deseja excluir a tarefa?.</v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="red darken-3"
            text
            @click="$emit('FechaModal')"
          >
            Cancelar
          </v-btn>
          <v-btn
            color="primary"
            text
            @click="handleDelete()"
          >
            Excluir
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
    props:['tarefa'],
     data () {
      return {
        dialog: true,
      }
    },
    methods:{
      handleDelete(){
        this.$store.dispatch('removeTarefa', this.tarefa.id);
        this.$emit('FechaModal');
      }
    }
 
}
</script>

<style>

</style>