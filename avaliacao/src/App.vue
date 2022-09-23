<template>
  <div>
    <form>
      <label for="Nota1"> Nome aluno  </label>
      <input type="text" id="nomeAluno" size="30" v-model="aluno"><br/>
      <br/>  
      <br/> 
      <label for="Nota1"> Nota 1  </label>
      <input type="text" id="primeiraNota" size="10" v-model="listaAlunos.nota1"><br/>
      <br/>
      <label for="Nota2"> Nota 2  </label>
      <input type="text" id="segundaNota" size="10" v-model="listaAlunos.nota2"><br/>
      <br/>
      <label for="Nota3"> Nota 3  </label>
      <input type="text" id="segundaNota" size="10" v-model="listaAlunos.nota3"><br/>  
      <br/>
      <br/>
      <button @click="adicionaAluno()">Cálculo de Media</button>   
    </form>
  </div>
  <br/>
  <br/>
  <br/>
  <br/>
  <div>
    <table>
      <tr>
        <th>Aluno</th>
        <th>Média</th>
        <th>Status</th>
      </tr>
      <tr v-for="aluno in listaAlunos" :key="aluno.aluno"> 
        <!-- coloca o estilo caso o isSelected seja true -->
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
        aluno : '',
        nota1 : 0.0,
        nota2 : 0.0,
        nota3 : 0.0,

      listaAlunos : [{
        aluno : 'teste',
        nota1 : 1.0,
        nota2 : 2.0,
        nota3 : 10.0,
        media : this.calculaMedia(),
        status : this.verificaStatus()
      }]
  }
 },

 methods : {
   calculaMedia() {
      let ma = (this.nota1 + this.nota2 * 2 + this.nota3 * 3)/7
      this.media = ma
      console.log(this.media)        
    },
    
    adicionaAluno() {
       this.listaAlunos.push({
          aluno : this.aluno,
          nota1 : this.nota1,
          nota2 : this.nota2,
          nota3 : this.nota3
        })
      console.log(this.listaAlunos)
    },

    verificaStatus() {
      if (this.media >= 7.0) {
            this.status = 'aprovado'
          }
          else {
            'reprovado'
          }
    }
 }



}
</script>

<style>
#app {

}
</style>
