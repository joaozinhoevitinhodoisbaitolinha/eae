<template>
  <div>
      <v-menu offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          v-bind="attrs"
          v-on="on"
          icon
        >
            <v-icon>
                 mdi-dots-vertical
            </v-icon>
        </v-btn>
      </template>
      <v-list>
        <v-list-item
          v-for="(item, index) in items"
          :key="index"
          @click="item.click()"
        >
          <v-icon left>{{ item.icone }}</v-icon>

          <v-list-item-title>{{ item.title }}</v-list-item-title>

        </v-list-item>
      </v-list>
    </v-menu>

    <ModalEditar
    v-if="items[0].modal"
    @FechaModal="items[0].modal = false"
    :tarefa="tarefa"
    />

    <ModalDelete
    v-if="items[1].modal"
    @FechaModal="items[1].modal = false"
    :tarefa="tarefa"
    />
  </div>
</template>

<script>
import ModalDelete from '../Modal/ModalDelete.vue'
import ModalEditar from '../Modal/ModalEditar.vue'
export default {
    props:['tarefa'],
    components:{ ModalEditar , ModalDelete },
    data: () => ({
      items: [
        { 
          icone:"mdi-pencil", 
          title: 'Editar',
          modal: false,
          click(){
              this.modal = true
          } 
        },
        { 
          icone:"mdi-trash-can", 
          title: 'Excluir',
          modal:false,
          click(){
              this.modal = true
          } 
        },
      ],
    }),
    
}
</script>

<style>

</style>