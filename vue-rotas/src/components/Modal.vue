<template>
    <div class="conteiner-modal">
        <div class="divHeaderModal">
          <p>Criar uma Tarefa</p>
          <button class="button-close-modal" @click="closeModal">
            X
          </button>
        </div>

        

        <input
          class="inputNomeTarefa"
          type="text"
          placeholder="Nome da Tarefa"
          name="nomeTarefa"
          v-model.trim.lazy="tarefa.nome"
        />

        <div class="inputData">
          <input
            type="date"
            placeholder="Data de inicio"
            name="DataInicioTarefa"
            v-model.lazy="tarefa.dataInicio"
          />

          <input
            type="date"
            placeholder="Data de término"
            name="DataTerminoTarefa"
            v-model.lazy="tarefa.dataTermino"
          />
        </div>

        <div class="divButtonCriarTarefa">
          <button class="ButtonCriarTarefa" v-if="action === 'add'" type="button" @click="addTarefa">Criar Tarefa</button>
          <button v-if="action === 'edit'" type="button" @click="editTask">Editar Tarefa</button>
          <button v-if="action === 'delete'" type="button" @click="deleteTask">Excluir Tarefa</button>
          <button v-if="action === 'complete'" type="button" @click="completeTask">Concluir Tarefa</button>
        </div>
      </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    tarefas: [],

    tarefa: {
        id: "",
        nome: "",
        dataInicio: "",
        dataTermino: "",
        completa: false,
      },
  }
}
</script>