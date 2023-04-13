<script setup>
import { ref } from 'vue'

const nome = ref('')
const dataNascimento = ref('')
const email = ref('')
const senha = ref('')
const confirmarSenha = ref('')
const rua = ref('')
const numeroCasa = ref('')
const bairro = ref('')
const cidade = ref('')
const estado = ref('')
const hobbies = ref('')
const linguagensProg = ref('')
const biografia = ref('')
const enviar = ref(false)
const mensagemErro = ref('')
const user = ref({avatar: null})

function handleFileUpload(e) {
  const target = e.target
  if (target && target.files) {
    const file = target.files[0]
    user.value.avatar = URL.createObjectURL(file)
  }
}
function confirmacao() {
  if (senha.value === confirmarSenha.value) {
    mensagemErro.value = ''
    return true
  } else {
    mensagemErro.value = 'As '
    return false
  }
}
</script>

<template>
  <div class="blo1">
    <form @submit.prevent="enviar = confirmacao()">
      <h1>Edição de Perfil</h1>
      <h3>Informações pessoais</h3>
      <div>
        <h3>Escolha sua nova foto de perfil</h3>
        <input type="file" id="avatarField" @change="handleFileUpload($event)"/>
      </div>
      <div>
        <input type="text" v-model="nome" v-on:keypress="enviar = false" placeholder="Digite seu nome..." required />
      </div>
      <div>
        <h4>Insira sua data de Nascimento:</h4>
        <input type="date" v-model="dataNascimento" v-on:keypress="enviar = false" required />
      </div>
      <div>
        <input type="email" v-model="email" v-on:keypress="enviar = false" placeholder="Digite seu e-mail..." required />
      </div>
      <hr />
      <h3>Informações de senha</h3>
      <div>
        <input type="password" v-model="senha" v-on:keypress="enviar = false" placeholder="Digite sua senha..."
          required />
      </div>
      <div>
        <input type="password" v-model="confirmarSenha" v-on:keypress="enviar = false" placeholder="Confirme sua senha..."
          required />
      </div>
      <hr />
      <h3>Informações de endereço</h3>
      <div>
        <input type="text" v-model="rua" v-on:keypress="enviar = false" required placeholder="Digite sua rua..." />
      </div>
      <div>
        <input type="number" v-model="numeroCasa" v-on:keypress="enviar = false" required min="1"
          placeholder="Número da sua casa..." />
      </div>
      <div>
        <input type="text" v-model="bairro" v-on:keypress="enviar = false" required placeholder="Digite seu bairro..." />
      </div>
      <div>
        <input type="text" v-model="cidade" v-on:keypress="enviar = false" required placeholder="Digite sua cidade..." />
      </div>
      <div>
        <h4>Insira seu estado:</h4>
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
        <h4>Insira seus Hobbies:</h4>
        <textarea v-model="hobbies" v-on:keypress="enviar = false"></textarea>
      </div>
      <div>
        <label for="linguagem">Diga quais são as suas linguagens de programação:</label>
        <input type="checkbox" v-model="cores" value="PY" /> Python
        <input type="checkbox" v-model="cores" value="C#" /> C#
        <input type="checkbox" v-model="cores" value="C++" /> C++
        <input type="checkbox" v-model="cores" value="C" /> C
        <input type="checkbox" v-model="cores" value="JV" /> Java
        <input type="checkbox" v-model="cores" value="JS" /> JavaScript
        <input type="checkbox" v-model="cores" value="PHP" /> PHP
        <input type="checkbox" v-model="cores" value="SW" /> Swift
        <input type="checkbox" v-model="cores" value="Go" /> Go
        <input type="checkbox" v-model="cores" value="SQL" /> SQL
        <input type="checkbox" v-model="cores" value="RB" /> Ruby
        <input type="checkbox" v-model="cores" value="TS" /> TypeScript
      </div>
      <div>
        <h4>Insira uma Biografia:</h4>
        <textarea v-model="biografia" v-on:keypress="enviar = false"></textarea>
      </div>
      <button type="submit">Enviar</button>
    </form>
    <p>{{ mensagemErro }}</p>
  </div>

  <div v-if="enviar">
    <h1>Perfil Atualizado:</h1>
    <div><img :src="user.avatar" /></div>
    <div>
      <p>{{ nome }}</p>
    </div>
    <div>
      <p>{{ dataNascimento }}</p>
    </div>
    <div>
      <p>{{ email }}</p>
    </div>
    <div></div>
    <div>
      <p>
        Endereço: {{ rua }}, {{ numeroCasa }}, {{ bairro }}, {{ cidade }},
        {{ estado }}
      </p>
    </div>
    <div>Hoobie(s): {{ hobbies }}</div>
    <div>Linguagem(s) de Programação: {{ linguagensProg }}</div>
    <div>Biografia: {{ biografia }}</div>
  </div>
</template>
<style scoped>
.blo1{
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 50px;
}
#avatarField{

}
</style>
