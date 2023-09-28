# hackaton.js

/* Atividade Hackaton – Algoritmos de Ordenação
1. Introdução
Sua equipe foi desafiada a criar um sistema de ordenação, pelo algoritmo Heapsort,
para uma base de dados de objetos, ou seja, um sistema em que dado um conjunto 
de informação a mesma é ordena em ordem crescente ou decrescente, conforme a 
escolha do usuário.
O sistema a ser desenvolvido está descrito no item 2 deste documento; o item 3 
mostra o que deve ser apresentado; e, por fim, o item 4 apresenta os testes a serem 
realizados.
2. Sistema
O sistema a ser desenvolvido possui os seguintes requisitos:
1. A linguagem a ser utilizada deve ser Javascript e rodar sobre Node.js;
2. Deve possuir um menu com as seguintes opções e funcionalidades:
a. Ordenar por ID: ordena os elementos pelo campo id;
b. Ordenar por NOME: ordena os elementos pelo campo nome;
c. Ordenar por IDADE: ordena os elementos pelo campo idade;
d. Ordenação: permite o usuário escolher o tipo de ordenação das 
informações (crescente ou decrescente). Por padrão, ao iniciar o 
sistema a ordenação é crescente.
3. A ordenação deve ser visualizada sempre no sistema.
3. Entrega
A equipe deve entregar o código fonte do sistema, devidamente comentad */

// Grupo: Eduardo Mello Garcia, Guilherme da Rocha Souza, Lucas Oliveira Barbosa

 const prompt = require('prompt-read') 

// Variável de controle
let sair;

// Banco de Dados
const pessoas = [
    { id: 1, nome: "Isaac Newton", idade: 28 },
    { id: 2, nome: "Friedrich Gauss", idade: 33 },
    { id: 3, nome: "Marie Curie", idade: 29 },
    { id: 4, nome: "Hedy Lamarr", idade: 23 },
    { id: 5, nome: "Albert Einstein", idade: 39 },
    { id: 6, nome: "Nicolau Copernico", idade: 30 },
    { id: 7, nome: "Galileu Galilei", idade: 25 },
    { id: 8, nome: "Alexander Volta", idade: 36 },
    { id: 9, nome: "André-Marie Ampère", idade: 23 },
    { id: 10, nome: "James Clerk Maxwell", idade: 25 },
    { id: 11, nome: "James Prescott Joule", idade: 33 },
    { id: 12, nome: "James Watt", idade: 23 },
    { id: 13, nome: "Archimedes de Siracusa", idade: 39 },
    { id: 14, nome: "Simom Ohm", idade: 35 }
]

const pressioneParaContinuar = () => prompt("pressione qualquer tecla para continuar...")

function exibirMenu() {
  console.log('Menu')
  console.log('=========================')
  console.log('1 - Ordenar por ID')
  console.log('2 - Ordenar por NOME')
  console.log('3 - Ordenar por IDADE')
  console.log('9 - Sair')
}

const selecionaDirecao = () => prompt("Deseja que a lista seja ordenada de forma crescente (S/n)? ").toLowerCase() !== 'n'

function checarDirecaoOrdenacao (valor1, valor2, crescente) {
  return crescente ? valor1 > valor2 : valor1 < valor2
}

// Função para ajustar um heap com base em um nó raiz
function organizarHeap(array, tamanhoArray, i, atributo, crescente) {
  let posicaoAtual = i;
  const esquerda = 2 * i + 1;
  const direita = 2 * i + 2;

  // Encontrar o elemento da posição atual entre o nó atual, o nó da esquerda e o nó da direita
  if (esquerda < tamanhoArray && checarDirecaoOrdenacao(array[esquerda][atributo], array[posicaoAtual][atributo], crescente)) {
    posicaoAtual = esquerda;
  }

  if (direita < tamanhoArray && checarDirecaoOrdenacao(array[direita][atributo], array[posicaoAtual][atributo], crescente)) {
    posicaoAtual = direita;
  }

  // Se a posição atual não for o nó raiz, troque-os
  if (posicaoAtual !== i) {
    const aux = array[i]
    array[i] = array[posicaoAtual]
    array[posicaoAtual] = aux
    // Continuar ajustando o heap recursivamente
    organizarHeap(array, tamanhoArray, posicaoAtual, atributo, crescente);
  }
}

// Função principal do Heapsort
function heapSort(array, atributo, crescente) {
  const tamanhoArray = array.length;

  // Construir um heap inicial baseado na direção selecionada
  for (let i = Math.floor(tamanhoArray / 2) - 1; i >= 0; i--) {
    organizarHeap(array, tamanhoArray, i, atributo, crescente);
  }

  // Extrair elementos um por um do heap e reconstruir o heap
  for (let i = tamanhoArray - 1; i > 0; i--) {
    // Trocar o elemento raiz com o último elemento
    const aux = array[0]
    array[0] = array[i]
    array[i] = aux
    // Chamar organizarHeap na pilha reduzida
    organizarHeap(array, i, 0, atributo, crescente);
  }
}

function ordenarPorAtributoSelecionado(atributo) {
  crescente = selecionaDirecao()
  heapSort(pessoas, atributo, crescente)
  console.log(pessoas)
  pressioneParaContinuar()
  console.clear()
  exibirMenu()
}

// Switch para seleção de opção do menu
function selecionarOpcao(opcao) {
  let atributo, crescente

  switch(opcao) {
    case 1:
      ordenarPorAtributoSelecionado('id')
      break
    case 2:
        ordenarPorAtributoSelecionado('nome')
        break
    case 3:
        ordenarPorAtributoSelecionado('idade')
        break
    case 9:
        sair = true
        console.clear()
        break
    default:
        console.log("Opção inválida")
        pressioneParaContinuar()
        console.clear()
        exibirMenu()
        break
  }
}

//MAIN
exibirMenu()
while(!sair) {
  const opcao = prompt("Digite a opção desejada: ", "number")
  selecionarOpcao(opcao)
}
