<template>
  <div>
    <h1>{{titulo}}</h1>
    <input type="text" placeholder="Nome do Aluno" v-model="nome" 
    v-on:keyup.enter="addAluno()">

    <table border="1px">
      <thead>
        <th>Matricula</th>
        <th>Nome</th>
        <th>Opções</th>
      </thead>
      <tbody>
        <tr v-for="(aluno, index) in alunos" :key="index">
          <td>{{index+1}}</td>
          <!--td>{{aluno.id}}</td>-->
          <td>{{aluno.nome}}</td>
          <td><button class="btn" @click="removerAluno(aluno)">Remover</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data()  {
    return{
      titulo: "Aluno",
      nome: '',
      alunos: [
        {id: 1, nome:'Matheus'},
        {id: 2, nome:'Laissa'}
        ],
    }
  },
  props: {
  },
  methods: {
    addAluno() {
      let _aluno = {
        nome : this.nome 
      }
      this.alunos.push(_aluno);
      console.log("-------");
      this.alunos.forEach(aluno => {
        console.log(aluno);
      });
      this.nome = ''
    },
    removerAluno(aluno) {
      let indice = this.alunos.indexOf(aluno);
      console.log('Aluno removido: ' + aluno.nome)
      this.alunos.splice(indice, 1);
    }
  },
}
</script>

<!-- Adicione o atributo "scoped" para limitar o CSS apenas a este componente -->
<style scoped>

</style>
