<template>
  <!-- <div class="home">    
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div class="todo">
    <hr style="width: 335px" />
    <div class="esquema2">
      <hr />
    </div>
    <div v-if="this.tarefas.length === 0" class="mensagem">
      <p>Nenhuma tarefa a fazer</p>
    </div>

    <div v-if="this.tarefas.length > 0">
      <div class="div_tarefas" v-for="tarefa in tarefas" :key="tarefa.nome">
        <div>
          <div class="div_nomeTarefa">
            <p class="p_nomeTarefa">{{ tarefa.nome }}</p>
          </div>

          <div class="div_datasTarefas">
            <p>{{ returnFormattedDate(tarefa.dataInicio) }} at</p>
            <br />
            <p>é {{ returnFormattedDate(tarefa.dataTermino) }}</p>
          </div>
        </div>
        <div class="div_botoes_editarTarefa">
          <svg
          @click="changeShowModal(true, 'edit', tarefa)"
          style="cursor: pointer;"
            width="15"
            height="17"
            viewBox="0 0 15 17"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M8.30294 4.27088C8.56199 3.94767 8.50997 3.47565 8.18675 3.21661C7.86354 2.95756 7.39152 3.00958 7.13248 3.33279L8.30294 4.27088ZM1.57396 11.4675L2.14199 11.9572C2.14785 11.9504 2.15358 11.9435 2.15919 11.9365L1.57396 11.4675ZM1.39583 11.9029L0.64729 11.8541L0.646636 11.8682L1.39583 11.9029ZM1.25 15.0518L0.500803 15.0171C0.499078 15.0544 0.500133 15.0917 0.503958 15.1288L1.25 15.0518ZM2.06979 15.7675L2.09431 16.5171C2.14433 16.5154 2.19406 16.5088 2.24275 16.4972L2.06979 15.7675ZM5.19479 15.0268L5.36777 15.7567L5.37941 15.7538L5.19479 15.0268ZM5.59583 14.7727L6.17444 15.25L6.18094 15.2419L5.59583 14.7727ZM12.4726 7.39604C12.7317 7.0729 12.6798 6.60087 12.3567 6.34173C12.0336 6.0826 11.5615 6.13449 11.3024 6.45763L12.4726 7.39604ZM7.13576 3.3326C6.8766 3.65572 6.92846 4.12776 7.25159 4.38691C7.57472 4.64607 8.04675 4.59421 8.30591 4.27108L7.13576 3.3326ZM9.375 1.73934L9.96007 2.20858C9.96993 2.19629 9.9794 2.18369 9.98846 2.1708L9.375 1.73934ZM11.0719 1.406L11.5517 0.829564C11.5278 0.809683 11.5027 0.791306 11.4765 0.774539L11.0719 1.406ZM13.4021 3.34559L13.9329 2.81575C13.9166 2.79944 13.8996 2.78389 13.8819 2.76915L13.4021 3.34559ZM13.7531 4.20067L14.503 4.20479V4.20479L13.7531 4.20067ZM13.3927 5.05184L12.8677 4.5162C12.8465 4.53703 12.8265 4.55911 12.8078 4.58233L13.3927 5.05184ZM11.3026 6.45733C11.0433 6.78033 11.095 7.25239 11.418 7.5117C11.741 7.771 12.2131 7.71936 12.4724 7.39635L11.3026 6.45733ZM8.46255 3.69069C8.40117 3.28105 8.01932 2.99873 7.60968 3.06012C7.20004 3.12151 6.91773 3.50335 6.97911 3.91299L8.46255 3.69069ZM11.9885 7.67001C12.3989 7.61424 12.6864 7.2363 12.6307 6.82586C12.5749 6.41542 12.197 6.1279 11.7865 6.18367L11.9885 7.67001ZM7.13248 3.33279L0.988726 10.9984L2.15919 11.9365L8.30294 4.27088L7.13248 3.33279ZM1.00593 10.9777C0.794362 11.2231 0.668508 11.5308 0.647423 11.8541L2.14424 11.9517C2.14411 11.9537 2.14332 11.9557 2.14199 11.9572L1.00593 10.9777ZM0.646636 11.8682L0.500803 15.0171L1.9992 15.0865L2.14503 11.9376L0.646636 11.8682ZM0.503958 15.1288C0.587353 15.9373 1.28192 16.5436 2.09431 16.5171L2.04527 15.0179C2.02012 15.0187 1.99862 14.9999 1.99604 14.9749L0.503958 15.1288ZM2.24275 16.4972L5.36775 15.7566L5.02183 14.2971L1.89683 15.0377L2.24275 16.4972ZM5.37941 15.7538C5.69121 15.6746 5.96967 15.4981 6.17438 15.2499L5.01728 14.2954C5.01545 14.2976 5.01296 14.2992 5.01017 14.2999L5.37941 15.7538ZM6.18094 15.2419L12.4726 7.39604L11.3024 6.45763L5.01073 14.3035L6.18094 15.2419ZM8.30591 4.27108L9.96007 2.20858L8.78993 1.2701L7.13576 3.3326L8.30591 4.27108ZM9.98846 2.1708C10.1425 1.95178 10.4418 1.89299 10.6672 2.03747L11.4765 0.774539C10.5747 0.196634 9.37772 0.431773 8.76154 1.30787L9.98846 2.1708ZM10.5921 1.98245L12.9223 3.92203L13.8819 2.76915L11.5517 0.829564L10.5921 1.98245ZM12.8713 3.87543C12.9563 3.9606 13.0037 4.07621 13.0031 4.19655L14.503 4.20479C14.5059 3.68426 14.3006 3.18416 13.9329 2.81575L12.8713 3.87543ZM13.0031 4.19655C13.0024 4.31688 12.9537 4.43197 12.8677 4.5162L13.9177 5.58748C14.2894 5.22313 14.5002 4.72532 14.503 4.20479L13.0031 4.19655ZM12.8078 4.58233L11.3026 6.45733L12.4724 7.39635L13.9776 5.52135L12.8078 4.58233ZM6.97911 3.91299C7.34049 6.32451 9.57223 7.99832 11.9885 7.67001L11.7865 6.18367C10.1832 6.40152 8.70234 5.29086 8.46255 3.69069L6.97911 3.91299Z"
              fill="#202D41"
            />
          </svg>

          <svg
          @click="changeShowModal(true, 'delete', tarefa)"
          style="cursor: pointer;"
            width="13"
            height="17"
            viewBox="0 0 13 17"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M10.8406 5.37513H2.1594C1.68017 5.37513 1.29169 5.76361 1.29169 6.24284V13.1876C1.29169 14.6259 2.45761 15.7918 3.89585 15.7918H9.10419C9.79486 15.7918 10.4572 15.5174 10.9456 15.0291C11.434 14.5407 11.7084 13.8783 11.7084 13.1876V6.24284C11.7084 5.76361 11.3199 5.37513 10.8406 5.37513Z"
              stroke="#202D41"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M9.625 3.29175L9.51458 3.07196C8.94365 1.92983 7.77637 1.20833 6.49948 1.20833C5.22259 1.20833 4.05531 1.92983 3.48437 3.07196L3.375 3.29175H9.625Z"
              stroke="#202D41"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M5.51356 8.847C5.51356 8.43279 5.17778 8.097 4.76356 8.097C4.34935 8.097 4.01356 8.43279 4.01356 8.847H5.51356ZM4.01356 12.3189C4.01356 12.7331 4.34935 13.0689 4.76356 13.0689C5.17778 13.0689 5.51356 12.7331 5.51356 12.3189H4.01356ZM8.98648 8.847C8.98648 8.43279 8.65069 8.097 8.23648 8.097C7.82227 8.097 7.48648 8.43279 7.48648 8.847H8.98648ZM7.48648 12.3189C7.48648 12.7331 7.82227 13.0689 8.23648 13.0689C8.65069 13.0689 8.98648 12.7331 8.98648 12.3189H7.48648ZM9.62502 2.54179C9.21081 2.54179 8.87502 2.87758 8.87502 3.29179C8.87502 3.70601 9.21081 4.04179 9.62502 4.04179V2.54179ZM11.7084 4.04179C12.1226 4.04179 12.4584 3.70601 12.4584 3.29179C12.4584 2.87758 12.1226 2.54179 11.7084 2.54179V4.04179ZM3.37502 4.04179C3.78923 4.04179 4.12502 3.70601 4.12502 3.29179C4.12502 2.87758 3.78923 2.54179 3.37502 2.54179V4.04179ZM1.29169 2.54179C0.877473 2.54179 0.541687 2.87758 0.541687 3.29179C0.541687 3.70601 0.877473 4.04179 1.29169 4.04179V2.54179ZM4.01356 8.847V12.3189H5.51356V8.847H4.01356ZM7.48648 8.847V12.3189H8.98648V8.847H7.48648ZM9.62502 4.04179H11.7084V2.54179H9.62502V4.04179ZM3.37502 2.54179H1.29169V4.04179H3.37502V2.54179Z"
              fill="#202D41"
            />
          </svg>

          <svg
          @click="changeShowModal(true, 'complete', tarefa)"
          style="cursor: pointer;"
            width="17"
            height="17"
            viewBox="0 0 17 17"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M1.20831 8.50019C1.20856 5.02154 3.66607 2.02749 7.07792 1.34907C10.4898 0.670644 13.9057 2.4968 15.2368 5.71074C16.5678 8.92467 15.4432 12.6313 12.5507 14.5637C9.65817 16.4962 5.80338 16.1163 3.34373 13.6564C1.97631 12.2889 1.20817 10.4341 1.20831 8.50019Z"
              stroke="#202D41"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M4.85413 8.50019L7.28433 10.9304L12.1458 6.06999"
              stroke="#202D41"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
      </div>
    </div>

    <div v-if="showModal" class="divCriarTarefa">
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
    </div>

    <div class="divPop">
      <button @click="changeShowModal(true, 'add')" class="buttonAbrirPopup">+</button>
    </div>
  </div>
  
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue';
// import Modal from '../components/Modal.vue'

export default {
  name: 'ToDo',
  // components: {
  //   HelloWorld,
  //   Modal
  // }
  data() {
    return {

      tarefas: [],

      tarefa: {
        id: "",
        nome: "",
        dataInicio: "",
        dataTermino: "",
        completa: false,
      },

      showModal: false,

      action: "add",
    };
  },
  methods: {
    teste() {
      return moment().format("MMMM Do YYYY, h:mm:ss a");
    },
    changeShowModal(showModal, action, tarefa) {
      this.showModal = showModal;
      this.action = action;
      if(tarefa?.id) {
        this.tarefa = tarefa
      }
      console.log("action ", action)
    },
    closeModal() {
      this.changeShowModal(false, "add")
      this.resetTask();
    },

    addTarefa(event) {
      const tarefaEnviada = Object.assign({}, this.tarefa);
      tarefaEnviada.id = uuidv4();
      this.tarefas.push(tarefaEnviada);
      sessionStorage.setItem("tarefas", JSON.stringify(this.tarefas));
      this.showModal = false;
      this.resetTask();
    },
    resetTask() {
      this.tarefa = {
        id: "",
        nome: "",
        dataInicio: "",
        dataTermino: "",
        completa: false,
      };
    },

    editTask() {
      
      const tasks = JSON.parse(sessionStorage.getItem("tarefas")) || [];
      const index = tasks.findIndex((t) => t.id === this.tarefa.id);
      if (index === -1) return;      
      tasks[index] = this.tarefa;      
      sessionStorage.setItem("tarefas", JSON.stringify(tasks));
      this.closeModal();
      this.getTasks();
    },

    deleteTask() {

      const tasks = JSON.parse(sessionStorage.getItem("tarefas")) || [];
      const index = tasks.findIndex((t) => t.id === this.tarefa.id);
      if (index === -1) return;
      tasks.splice(index, 1);
      sessionStorage.setItem("tarefas", JSON.stringify(tasks));
      this.closeModal();
      this.getTasks();
    },

    completeTask() {
      const tasks = JSON.parse(sessionStorage.getItem("tarefas")) || [];
      const index = tasks.findIndex((t) => t.id === this.tarefa.id);
      if (index === -1) return;
      tasks[index].completa = true;
      sessionStorage.setItem("tarefas", JSON.stringify(tasks));
      this.closeModal();
      this.getTasks();
    },

    getTasks() {
      
      // As tarefas não podem estar com completed: true
      // As tarefas não podem estar com a data final com o dia anterior ao dia de hoje
      this.tarefas = []
      console.log(this.tarefas)

      const tasks = JSON.parse(sessionStorage.getItem("tarefas")) || [];
      console.log(tasks)

      if(tasks.length === 0) return;
      const toDoTasks = tasks.filter(task => {
        const today = moment().format("YYYY-MM-DD")
        const endDate = task.dataTermino
        return moment(today).isSameOrBefore(endDate) && !task.completa

      })
      console.log(toDoTasks)

      this.tarefas = toDoTasks;
    },

    returnFormattedDate(date) {
      return moment(date).format("DD/MM/YYYY");
    },
  },
  mounted() {
    this.getTasks();
  },
}
</script>
