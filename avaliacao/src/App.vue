<template>
  <div>
    <form @submit.prevent="adicionaAluno()">
      <label for="Nota1"> Nome aluno  </label>
      <input type="text" id="nomeAluno" size="30" v-model="aluno"><br/>
      <br/>  
      <br/> 
      <label for="Nota1"> Nota 1  </label>
      <input type="text" id="primeiraNota" size="10" v-model="nota1"><br/>
      <br/>
      <label for="Nota2"> Nota 2  </label>
      <input type="text" id="segundaNota" size="10" v-model="nota2"><br/>
      <br/>
      <label for="Nota3"> Nota 3  </label>
      <input type="text" id="segundaNota" size="10" v-model="nota3"><br/>  
      <br/>
      <br/>
      <input type="submit" value="Cálculo de Media"/>
    </form>
  <br/>
  <br/>
  <br/>
  <br/>
    <table>
      <tr>
        <th>Aluno</th>
        <th>Média</th>
        <th>Status</th>
      </tr>
      <tr v-for="aluno in listaAlunos" :key="aluno.listaAlunos" @click="adicionaAluno(aluno)" :class=" {'aprovado' : verificaStatus(aluno.status)}"> 
        <td>{{ aluno.aluno }}</td>
        <td>{{ aluno.media }}</td>
        <td>{{ aluno.status }} </td>
      </tr>
    </table>
  </div>
</template>

<script>


export default {
 data () {
  return {
      listaAlunos : [{
        aluno : '',
        nota1 : 0,
        nota2 : 0,
        nota3 : 0,
        media : this.calculaMedia(),
        status : this.verificaStatus()
      }]
  }
 },

 methods : {
   calculaMedia() {
      this.media = ( this.nota1 + (this.nota2 * 2) + (this.nota3 * 3) ) / 6  
      return this.media    
    },
    
    adicionaAluno() {
       this.listaAlunos.push({
          aluno : this.aluno,
          nota1 : this.nota1,
          nota2 : this.nota2,
          nota3 : this.nota3,
          media : this.calculaMedia(),
          status : this.verificaStatus()
        })
    },

    verificaStatus() {
      if (this.media >= 7.0) {
            return this.status = 'aprovado'
          }
          else {
            return this.status = 'reprovado'
          }
    }
 }



}
</script>

<style>
.aprovado{
  background-color: blue;
}

.reprovado{
  background-color: red;
}
</style>
