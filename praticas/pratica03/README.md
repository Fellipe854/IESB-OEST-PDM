<<<<<<< HEAD
# 💻 Prática 03: Interface Estática do To-Do List

Chegou a hora de dar uma “cara” ao aplicativo. Nesta prática você constrói a **UI** da lista de tarefas usando componentes core, `StyleSheet` e Flexbox. **Ainda sem** adicionar/remover de verdade — o foco é layout.

## 🎯 Objetivos

* Aplicar `View`, `Text`, `TextInput` e `TouchableOpacity`.
* Organizar layout com Flexbox (`column` e `row`).
* Criar estilos com `StyleSheet.create`.
* Entregar uma tela legível no Expo Go.

---

## 📦 Fluxo Git

1. Crie a Issue da **Prática 03**.
2. Crie a branch:

```bash
git checkout -b feature/pratica03
```

3. Trabalhe no projeto Expo desta pasta (`praticas/pratica03`).  
   Se ainda não existir app aqui, crie com `npx create-expo-app@latest` (como nas práticas anteriores) **ou** copie a base da Prática 02 e continue evoluindo.

```bash
npm install
npx expo start
```

---

## 🛠️ O que construir na tela

Limpe o conteúdo padrão do arquivo principal e monte:

### 1. Cabeçalho

* Título grande e em negrito: **Minhas Tarefas**

### 2. Área de inserção

* Um `<TextInput>` com placeholder (ex.: `Digite uma tarefa...`)
* Ao lado, um botão (`TouchableOpacity`) com texto `+` ou `Add`
* Use uma `View` com `flexDirection: 'row'` para alinhá-los na mesma linha

### 3. Lista estática (hardcoded)

Crie **2 ou 3 cards** fixos no JSX (ainda sem array dinâmico). Cada card deve ter:

* Um texto de tarefa (pode ser longo, para testar quebra de linha)
* Um botão/texto `X` (lixeira simbólica) — ainda sem função real

---

## 💡 Dicas de estilização

* Na `View` raiz: `flex: 1` e `padding` para afastar das bordas.
* No `TextInput`: `borderWidth`, `borderColor`, `borderRadius`, `padding`, `flex: 1`.
* Nos cards: fundo claro, `borderRadius`, `padding`, `marginBottom`, e `flexDirection: 'row'` entre texto e `X`.
* Use `StyleSheet.create` — evite deixar todos os estilos “inline” se a tela crescer.

Esqueleto mental:

```text
View (container)
 ├── Text (Minhas Tarefas)
 ├── View (row)
 │    ├── TextInput
 │    └── TouchableOpacity (+)
 └── View (lista)
      ├── View (card) → Text + TouchableOpacity (X)
      ├── View (card)
      └── View (card)
```

---

## ✅ Critérios de entrega

* [ ] Layout agradável e legível no celular (Expo Go)
* [ ] Título, input+botão em linha, e pelo menos 2 cards estáticos
* [ ] Estilos via `StyleSheet`
* [ ] Issue, branch `feature/pratica03`, commit, push e Pull Request

### Commit sugerido

```bash
git add .
git commit -m "Feat: Cria interface estatica do app de tarefas"
git push origin feature/pratica03
```

Na **Aula 04**, a interface ganha vida com **estado (`useState`)**: digitar, adicionar e remover tarefas de verdade.
=======
# 💻 Prática 03: Dando Vida ao App (Adicionar e Deletar Tarefas)

Chegou a hora da verdade! Vamos conectar a interface que construímos na Prática 02 com a lógica do React. Ao final desta prática, você conseguirá digitar uma tarefa, adicioná-la à lista na tela e excluí-la.

## 🛠️ O que deve ser feito

1. **Siga o Fluxo:** Crie a Issue da Prática 03, crie a branch `feature/pratica03`, instale as dependências e rode o projeto (`npx expo start`).
2. **Crie os Estados:** No topo do seu componente `App`, crie dois estados:
   * Um para armazenar o texto que o usuário está digitando (ex: `taskText`).
   * Um para armazenar o array/lista de tarefas (ex: `tasks`). Comece com um array vazio `[]`.
3. **Capture a Digitação:** No seu `<TextInput>`, adicione as propriedades `value={taskText}` e `onChangeText={setTaskText}`. Agora o input reflete o estado!
4. **Função de Adicionar:** Crie uma função `handleAdd()`. Ela deve:
   * Verificar se o input não está vazio.
   * Criar um objeto para a nova tarefa com um ID único (dica: use `Date.now().toString()`) e o texto digitado.
   * Usar a função de atualizar o array (Spread Operator `...`) para adicionar a tarefa.
   * Limpar o `taskText` para esvaziar o input.
5. **Renderize a Lista:** Em vez de usar cards "hardcoded", use a função `.map()` no seu array de `tasks` para renderizar os itens dinamicamente na tela. *(Aviso: Se a lista ficar muito grande, ela não vai rolar a tela ainda, resolveremos isso na próxima aula!)*
6. **Função de Deletar:** Crie uma função `handleDelete(id)`. Ela deve usar o `.filter()` para remover a tarefa com o ID correspondente e atualizar o estado da lista. Passe essa função para o botão de "X" de cada card.

## ✅ Como Entregar
1. Teste no seu celular: Adicione 3 tarefas diferentes e tente deletar a do meio.
2. Faça o commit: `git commit -m "Feat: Implementa useState para adicionar e remover tarefas"`
3. Faça o push para o GitHub e abra o seu **Pull Request** para a revisão do professor!
>>>>>>> 62a42f7 (Subindo o template para o repositório)
