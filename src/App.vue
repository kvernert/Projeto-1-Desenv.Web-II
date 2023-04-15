<script setup>
import { ref, computed, } from 'vue'

const nome = ref('')
const dtNascimento = ref('')
const email = ref('')
const senha = ref('')
const confirmarSenha = ref('')
const rua = ref('')
const numeroCasa = ref('')
const bairro = ref('')
const cidade = ref('')
const estado = ref('')
const hobbies = ref('')
const linguagensProg = ref([])
const biografia = ref('')
const enviar = ref(false)
const user = ref({
  avatar: null
})

const mensagemErro = computed(() => {
  if (senha.value != confirmarSenha.value) {
    return 'As senhas devem ser iguais'
  } else {
    return ''
  }
})
function confirmacao() {
  if (senha.value === confirmarSenha.value) {
    return true;
  } else {
    return false
  }
}
function handleFileUpload(e) {
  const target = e.target
  if (target && target.files) {
    const file = target.files[0]
    user.value.avatar = URL.createObjectURL(file)
  }
}

</script>

<template>
  <div class="container">
    <div class="info">
      <form @submit.prevent="enviar = confirmacao()">
        <h1>Edição de Perfil</h1>
        <h3>Informações Pessoais</h3>
        <div>
          <h3>Escolha sua nova foto de perfil</h3>
          <input type="file" @change="handleFileUpload($event)" />
        </div>
        <div>
          <h4>Informe seu nome:</h4>
          <input type="text" class="input-balao-up" v-model="nome" v-on:keypress="enviar = false" placeholder="Digite seu nome..." required />

        </div>
        <div>
          <h4>Informe sua Data de Nascimento:</h4>
          <input type="date" v-model="dtNascimento" v-on:keypress="enviar = false" required />
        </div>
        <h4>Informe seu E-mail: </h4>
        <div>
          <input type="email" class="input-balao-up" v-model="email" v-on:keypress="enviar = false" placeholder="Digite seu e-mail..."
            required />
           
        </div>
        <hr />
        <h3>Informações da Senha:</h3>
        <div>
          <input type="password" class="input-balao-up" v-model="senha" v-on:keypress="enviar = false" placeholder="Digite sua senha..."
            required />
            
        </div>
        <div>
          <input type="password" class="input-balao-up" v-model="confirmarSenha" v-on:keypress="enviar = false"
            placeholder="Confirme sua senha..." required />
          
        </div>
        <hr />
        <h3>Informações de Endereço:</h3>
        <div>
          <input type="text" class="input-balao-up" v-model="rua" v-on:keypress="enviar = false" required placeholder="Digite sua rua..." />
          
        </div>
        <div>
          <input type="number" class="input-balao-up" v-model="numeroCasa" v-on:keypress="enviar = false" required min="1"
            placeholder="Número da sua casa..." />
           
        </div>
        <div>
          <input type="text" class="input-balao-up" v-model="bairro" v-on:keypress="enviar = false" required
            placeholder="Digite seu bairro..." />
         
        </div>
        <div>
          <input type="text" class="input-balao-up" v-model="cidade" v-on:keypress="enviar = false" required
            placeholder="Digite sua cidade..." />
        
        </div>
        <div>
          <h4>Informe seu Estado:</h4>
          <select v-model="estado" v-on:keypress="enviar = false" required>
            <option value="AC">Acre(AC)</option>
            <option value="AL">Alagoas(AL)</option>
            <option value="AP">Amapá(AP)</option>
            <option value="AM">Amazonas(AM)</option>
            <option value="BA">Bahia(BA)</option>
            <option value="CE">Ceará(CE)</option>
            <option value="DF">Distrito Federal(DF)</option>
            <option value="ES">Espírito Santo(ES)</option>
            <option value="GO">Goiás(GO)</option>
            <option value="MA">Maranhão(MA)</option>
            <option value="MT">Mato Grosso(MT)</option>
            <option value="MS">Mato Grosso do Sul(MS)</option>
            <option value="MG">Minas Gerais(MG)</option>
            <option value="PA">Pará(PA)</option>
            <option value="PB">Paraíba(PB)</option>
            <option value="PR">Paraná(PR)</option>
            <option value="PE">Pernambuco(PE)</option>
            <option value="PI">Piauí(PI)</option>
            <option value="RJ">Rio de Janeiro(RJ)</option>
            <option value="RN">Rio Grande do Norte(RN)</option>
            <option value="RS">Rio Grande do Sul(RS)</option>
            <option value="RO">Rondônia(RO)</option>
            <option value="RR">Roraima(RR)</option>
            <option value="SC">Santa Catarina(SC)</option>
            <option value="SP">São Paulo(SP)</option>
            <option value="SE">Sergipe(SE)</option>
            <option value="TO">Tocantins(TO)</option>
          </select>
        </div>
        <hr />
        <div>
          <h4>Informe seus Hobbies:</h4>
          <textarea class="textarea-balao-up" v-model="hobbies" v-on:keypress="enviar = false"></textarea>
        
        </div>
        <hr />
        <div class="linguagens">
          <label for="linguagensProg">Diga quais são as suas linguagens de programação:</label>
          <div>
            <input type="checkbox" v-model="linguagensProg" value="PY" /> Python
            <input type="checkbox" v-model="linguagensProg" value="C#" /> C#
            <input type="checkbox" v-model="linguagensProg" value="C++" /> C++
            <input type="checkbox" v-model="linguagensProg" value="C" /> C
            <input type="checkbox" v-model="linguagensProg" value="JV" /> Java
            <input type="checkbox" v-model="linguagensProg" value="JS" /> JavaScript
            <input type="checkbox" v-model="linguagensProg" value="PHP" /> PHP
            <input type="checkbox" v-model="linguagensProg" value="SW" /> Swift
            <input type="checkbox" v-model="linguagensProg" value="Go" /> Go
            <input type="checkbox" v-model="linguagensProg" value="SQL" /> SQL
            <input type="checkbox" v-model="linguagensProg" value="RB" /> Ruby
            <input type="checkbox" v-model="linguagensProg" value="TS" /> TypeScript
          </div>
        </div>
        <div>
          <hr />
          <h4>Informe sua Biografia:</h4>
          <textarea class="textarea-balao-up" v-model="biografia" v-on:keypress="enviar = false"></textarea>
        
        </div>
        <button type="submit">Enviar</button>
      </form>
      <p>{{ mensagemErro }}</p>
    </div>

    <div v-if="enviar" class="info2">
      <h1>Perfil Atualizado:</h1>
      <div class="infoLado">
        <div>
          <img :src="user.avatar" />
          <div class="textoInfo">
            <p>Nome:{{ nome }}</p>
            <p>Data de Nascimento:{{ dtNascimento }}</p>
            <p>E-mail:{{ email }}</p>
          </div>
        </div>
        <div>Sua senha: {{ senha }}</div>
        <div v-if="rua!=''.trim() && numeroCasa!=''.trim() && bairro!=''.trim() && cidade!=''.trim() && estado!=''.trim()">
          <p>
            Endereço: {{ rua }}, {{ numeroCasa }}, {{ bairro }}, {{ cidade }},
            {{ estado }}
          </p>
        </div>
        <div v-if="hobbies!=''.trim()">Hoobie(s): {{ hobbies }}</div>
        <div  v-if="linguagensProg!=''.trim()">Linguagem(s) de Programação: {{ linguagensProg }}</div>
        <div  v-if="biografia!=''.trim()">Biografia: {{ biografia }}</div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.container {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
}

button {
  margin: 5px;
  font-weight: bold;
  width: 200px;
  background-color: rgb(119, 8, 56);
  color: rgb(183, 210, 219);
  border-radius: 10px;
  cursor: pointer;
}

.info {
  margin-top: 50px;
  padding: 10px;
  background-color: rgb(119, 8, 56);
  padding: 20px 30px;
  color: rgb(183, 210, 219);
  border-radius: 10px;
  width: 700px;
}

.info2 {
  width: 50%;
  margin-top: 50px;
  background-color: rgb(119, 8, 56);
  padding: 20px 30px;
  color: rgb(183, 210, 219);
  border-radius: 10px;
  width: 600px;
  height: 600px;
}

.linguagens {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
}

select{
  background-color: indianred;
  border-radius: 10px;
}


img {
  width: 100px;
  height: 150px;
  float: left;
  margin-right: 20px;
}

.infoLado {
  overflow: auto;
}

.textoInfo {
  display: inline-block;
}
.input-balao-up {
  display: inline-block;
  width: 40%;
  padding: 15px 0 10px 50px;
  font-family: "Open Sans", sans;
  font-weight: 400;
  color: #4C4C4C;
  background: #ffffff;
  border: 0;
  border-radius: 50px;
  outline: 0;
  transition: all .3s ease-in-out;
  box-shadow: 0 13px 8px -8px rgba(0, 0, 0, 0.5);
}
.input-balao-up::-webkit-input-placeholder {
  color:indianred;
  font-weight: 300;
}

.input-balao-up:focus,
.input-balao-up:active {
  color: #ffffff;
  padding: 15px 0 10px 25px;
  background: indianred;
}
.input-balao-up:focus::-webkit-input-placeholder,
.input-balao-up:active::-webkit-input-placeholder {
  color: #ffffff;
}
.textarea-balao-up {
  display: inline-block;
  width: 70%;
  height: 80px;
  padding: 15px 0 10px 50px;
  font-family: "Open Sans", sans;
  font-weight: 400;
  color: #4C4C4C;
  background: #ffffff;
  border: 0;
  border-radius: 50px;
  outline: 0;
  transition: all .3s ease-in-out;
  box-shadow: 0 13px 8px -8px rgba(0, 0, 0, 0.5);
}
.textarea-balao-up::-webkit-input-placeholder {
  color: indianred;
  font-weight: 300;
}
.textarea-balao-up:focus,
.textarea-balao-up:active {
  color: #ffffff;
  padding: 15px 0 10px 25px;
  background: indianred;
}
.textarea-balao-up:focus::-webkit-input-placeholder,
.textarea-balao-up:active::-webkit-input-placeholder {
  color: #ffffff;
}

</style>
