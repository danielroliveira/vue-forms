<template>
	<div id="app">
		<h1>Formulário Desafio</h1>
		<div class="conteudo">
			<form v-if="!submited" class="painel">
				<div class="cabecalho">Formulário</div>
				<nome-completo v-model="nomeCompleto"></nome-completo>
				<rotulo nome="e-mail">
					<slot>
						<input v-model="usuario.email" type="text">
					</slot>
				</rotulo>				
				<rotulo nome="senha">
					<slot>
						<input v-model="usuario.senha" type="password">
					</slot>
				</rotulo>
				<Rotulo nome="Armazenar Dados?">
					<span class="mr-4">
						<input type="radio" value=1 
						v-model="usuario.armazenar"> Sim
					</span>
					<span class="mr-4">
						<input type="radio" value=0 
						v-model="usuario.armazenar"> Não
					</span>
				</Rotulo>
				<button @click.prevent="submit" >Enviar</button>
			
				<!-- Exercicio 03 -->
				<!-- Crie um componente personalizado NomeCompleto -->
				<!-- Esse componente deve receber Nome e Sobrenome -->
			</form>
			<div v-else class="painel">
				<div class="cabecalho">Resultado</div>
				<Rotulo nome="Nome">
					<span>{{ nomeCompleto.nome }}</span>
				</Rotulo>
				<Rotulo nome="Sobrenome">
					<span>{{ nomeCompleto.sobrenome }}</span>
				</Rotulo>
				<Rotulo nome="e-mail">
					<span>{{ usuario.email }}</span>
				</Rotulo>
				<Rotulo nome="senha">
					<span>{{ usuario.senha }}</span>
				</Rotulo>
				<Rotulo nome="Armazenar dados">
					<span>{{ usuario.armazenar === 1 ? 'Sim' : 'Não' }}</span>
				</Rotulo>
			</div>
		</div>
	</div>
</template>

<script>
import Rotulo from './components/Rotulo.vue'
import nomeCompleto from './components/NomeCompleto.vue'

export default {
	name: 'app',
	components: { Rotulo, nomeCompleto },
	data() {
		return {
			submited: false,
			usuario: {
				email: '',
				senha: '',
				armazenar: 1,
			},
			nomeCompleto: {
				nome: '',
				sobrenome: '',
			}
		}
	},
	methods: {
		submit() {
			this.submited = true
		}
	}
}
</script>

<style>

body {
	background-color: #ECECEC;
}

#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;

	display: flex;
	flex-direction: column;
}

.conteudo {
	display: flex;
}

.painel {
	flex: 1;
	background: #FFF;
	margin: 0px 10px;
	padding: 20px;
	border: 1px solid #AAA;
	border-radius: 5px;
}

.painel .cabecalho {
	width: 100%;
	background-color: #DDD;
	padding: 10px 0px;
	border-radius: 5px;
	font-size: 1.4rem;
}

#app form button {
	float: right;
	margin: 10px 0px;
	padding: 10px 20px;
	font-size: 1.4rem;
	border-radius: 5px;
	color: #FFF;
	background-color: #2196F3;
}

#app h1 {
	font-weight: 200;
	margin: 20px;
	padding: 0;
}

.mr-4 {
	margin-right: 40px;
}
</style>
