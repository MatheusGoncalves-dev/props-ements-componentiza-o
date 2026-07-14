# 🟡 Nível 2 — Props, Emits e Componentização

## 🎯 Objetivo do nível
Aprender a quebrar a UI em componentes reutilizáveis que se comunicam entre si via `props` (pai → filho) e `emit` (filho → pai).

## 📁 Estrutura sugerida
src/components/
├── TodoForm.vue<br>
├── TodoItem.vue<br>
├── ProductCard.vue<br>
└── SearchFilter.vue
---

## 🧩 Desafio 5 — To-Do refatorado em componentes

**Objetivo:** dividir responsabilidades entre componentes.

### Requisitos
- [ ] Separe o To-Do do Nível 1 em dois componentes: `TodoForm.vue` (input + botão adicionar) e `TodoItem.vue` (cada item da lista)
- [ ] O componente pai (`App.vue` ou um novo `TodoList.vue`) guarda a lista de tarefas (o "estado")
- [ ] `TodoForm` emite um evento `@adicionar` com o texto digitado, o pai escuta e adiciona à lista
- [ ] `TodoItem` recebe a tarefa via `props` e emite `@remover` (e `@concluir`, se você fez o extra do Nível 1) para o pai

### Conceitos praticados
`defineProps()` · `defineEmits()` · comunicação pai → filho → pai

### Critério de "pronto"
O comportamento é idêntico ao do Nível 1, mas agora a lógica está espalhada em 3 componentes distintos, cada um com uma única responsabilidade.

---

## 🧩 Desafio 6 — Card de produto reutilizável

**Objetivo:** criar um componente genérico e reutilizável.

### Requisitos
- [ ] Componente `ProductCard.vue` que recebe via `props`: `nome`, `preco`, `quantidade`
- [ ] Exibe essas informações de forma organizada (pode estilizar como um "cartão")
- [ ] Emite um evento `@remover` quando o usuário clica num botão "Excluir"
- [ ] Emite um evento `@editar` quando clica em "Editar" (não precisa implementar a edição em si ainda, só emitir o evento)
- [ ] No componente pai, crie uma lista fixa de 3-4 produtos (array de objetos) e renderize um `ProductCard` para cada um com `v-for`

### Regra extra (opcional)
- [ ] Adicione uma prop `quantidadeMinima`; se `quantidade < quantidadeMinima`, mostre um aviso visual (ex: borda vermelha ou texto "Estoque baixo")

### Conceitos praticados
`props` tipadas · `emit` com dados · `v-for` + componentes

### Critério de "pronto"
Você vê múltiplos cards na tela, cada um refletindo dados diferentes, e consegue "remover" um card específico clicando no seu próprio botão de excluir.

---

## 🧩 Desafio 7 — Filtro de lista

**Objetivo:** aprender `computed` para derivar dados filtrados sem alterar a lista original.

### Requisitos
- [ ] Um campo de busca (`<input>`) acima da lista de produtos do Desafio 6
- [ ] Conforme o usuário digita, a lista exibida filtra apenas os produtos cujo nome contém o texto digitado (case-insensitive)
- [ ] A lista original (array de produtos) não deve ser alterada — use uma `computed` que retorna a versão filtrada

### Conceitos praticados
`computed()` · `.filter()` · `.toLowerCase()`

### Critério de "pronto"
Ao digitar parte do nome de um produto, apenas os cards correspondentes permanecem visíveis, em tempo real.
