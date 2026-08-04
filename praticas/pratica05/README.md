<<<<<<< HEAD
<<<<<<< HEAD
# 💻 Prática 05: FlatList e App que Não Esquece

Nesta prática o To-Do ganha lista eficiente e persistência local. **Ainda não** vamos extrair componentes — isso é a Prática 06.

## 🎯 Objetivos

* Substituir `.map()` por `FlatList`.
* Salvar e carregar tarefas com AsyncStorage + `useEffect`.
* Validar que fechar e reabrir o app mantém os dados.

---

## 📦 Fluxo Git

1. Crie a Issue da **Prática 05**.
2. Branch:

```bash
git checkout -b feature/pratica05
```

3. Trabalhe em `praticas/pratica05` (evolua a base da Prática 04).

```bash
npm install
npx expo start
```

---

## 🛠️ Parte A — FlatList

1. Remova o `.map()` da lista.
2. Importe `FlatList` de `react-native`.
3. Configure:

* `data={tasks}`
* `keyExtractor={(item) => item.id}`
* `renderItem={...}` desenhando cada tarefa (card ainda pode ficar inline no `App`)

4. Teste adicionando **muitas** tarefas (15+) e confirme a rolagem suave.

---

## 🛠️ Parte B — AsyncStorage

1. Pare o bundler (Ctrl+C) e instale:

```bash
npx expo install @react-native-async-storage/async-storage
```

2. Crie `saveTasks` (async): grave a lista com `setItem` + `JSON.stringify`.
3. Chame `saveTasks` após adicionar e após deletar (com a lista já atualizada).
4. Crie `loadTasks` (async): leia com `getItem`, faça `JSON.parse` se houver valor, e use `setTasks`.
5. No `useEffect` com `[]`, chame `loadTasks()` na montagem.

### Teste extremo

Adicione 3 tarefas → feche o app por completo (remover dos recentes) → abra de novo → as tarefas devem continuar lá.

---

## ✅ Critérios de entrega

* [ ] `FlatList` rolando com muitos itens
* [ ] Persistência: fechar e reabrir mantém as tarefas
* [ ] Add e delete continuam funcionando
* [ ] Issue, branch `feature/pratica05`, commit, push e Pull Request

### Commit sugerido

```bash
git add .
git commit -m "Feat: Adiciona FlatList e AsyncStorage para persistir tarefas"
git push origin feature/pratica05
```

Na **Aula 06**, vamos **organizar o código**: extrair o card da tarefa para um componente reutilizável com props.
=======
# 💻 Prática 05: Arrumando a Casa (Refatoração)
=======
# 💻 Prática 05: FlatList, Persistência e TaskCard
>>>>>>> 6e3395a (Atualizando as aulas)

Nesta prática o To-Do fica mais profissional: lista eficiente, dados que sobrevivem ao fechar o app, e código organizado em componente.

## 🎯 Objetivos

<<<<<<< HEAD
1. **Siga o Fluxo:** Crie a Issue da Prática 05, crie a branch `feature/pratica05` e rode o projeto (`npx expo start`).
2. **Crie a Estrutura de Pastas:** Na raiz do seu projeto, crie uma pasta chamada `src`. Dentro de `src`, crie uma pasta chamada `components`.
3. **Crie o Componente Card:** * Dentro de `src/components`, crie um arquivo chamado `TaskCard.js` (ou `.jsx`).
   * Recorte todo o código JSX (a `<View>`, o `<Text>` e o `<TouchableOpacity>`) que representa uma tarefa isolada lá do seu `App.js` e cole dentro deste novo arquivo.
   * Não esqueça de recortar os estilos (`StyleSheet`) referentes ao card e levá-los para este arquivo também!
4. **Configure as Props:**
   * O seu `TaskCard` precisa receber duas informações do pai para funcionar: o texto da tarefa e a função que será chamada ao clicar no botão de deletar.
   * Configure o componente para receber `{ title, onDelete }` via **props**.
5. **Importe no App.js:**
   * Volte ao seu `App.js` e importe o componente recém-criado: `import { TaskCard } from './src/components/TaskCard';`
   * Na sua `FlatList`, substitua o código antigo pela chamada do novo componente, passando as props corretamente:
   ```javascript
   renderItem={({ item }) => (
      <TaskCard 
         title={item.task} 
         onDelete={() => handleDelete(item.id)} 
      />
   )}
   ```
✅ **Como Entregar**
1. **Teste de Regressão**: Teste o app no seu celular. Ele **deve continuar funcionando exatamente igual** à aula passada (adicionando, deletando e salvando). Se algo parou, revise suas Props!
2. Faça o commit: `git commit -m "Refactor: Extrai interface da tarefa para componente TaskCard"`
3. Faça o push para o GitHub e abra o seu **Pull Request** para a revisão!
>>>>>>> 62a42f7 (Subindo o template para o repositório)
=======
* Substituir `.map()` por `FlatList`.
* Salvar e carregar tarefas com AsyncStorage + `useEffect`.
* Extrair o card para `src/components/TaskCard`.
* Garantir que o comportamento continue igual (teste de regressão).

---

## 📦 Fluxo Git

1. Crie a Issue da **Prática 05**.
2. Branch:

```bash
git checkout -b feature/pratica05
```

3. Trabalhe em `praticas/pratica05` (evolua a base da Prática 04).

```bash
npm install
npx expo start
```

---

## 🛠️ Parte A — FlatList

1. Remova o `.map()` da lista.
2. Importe `FlatList` de `react-native`.
3. Configure:

* `data={tasks}`
* `keyExtractor={(item) => item.id}`
* `renderItem={...}` desenhando cada tarefa

4. Teste adicionando **muitas** tarefas e confirme a rolagem suave.

---

## 🛠️ Parte B — AsyncStorage

1. Pare o bundler (Ctrl+C) e instale:

```bash
npx expo install @react-native-async-storage/async-storage
```

2. Crie `saveTasks` (async): grave a lista com `setItem` + `JSON.stringify`.
3. Chame `saveTasks` após adicionar e após deletar (com a lista já atualizada).
4. Crie `loadTasks` (async): leia com `getItem`, faça `JSON.parse` se houver valor, e use `setTasks`.
5. No `useEffect` com `[]`, chame `loadTasks()` na montagem.

### Teste extremo

Adicione 3 tarefas → feche o app por completo (remover dos recentes) → abra de novo → as tarefas devem continuar lá.

---

## 🛠️ Parte C — Componente `TaskCard`

1. Crie a pasta `src/components`.
2. Crie `src/components/TaskCard.js` (ou `.jsx`).
3. Recorte o JSX do card (e os estilos dele) para esse arquivo.
4. O componente deve receber props: `{ title, onDelete }`.
5. No `App`, importe e use na `FlatList`:

```javascript
import { TaskCard } from './src/components/TaskCard';

// ...
renderItem={({ item }) => (
  <TaskCard
    title={item.title}
    onDelete={() => handleDelete(item.id)}
  />
)}
```

> Se na prática anterior o campo se chamava `task` em vez de `title`, padronize para `title` **ou** adapte a prop — o importante é pai e filho falarem a mesma língua.

---

## ✅ Critérios de entrega

* [ ] `FlatList` rolando com muitos itens
* [ ] Persistência: fechar e reabrir mantém as tarefas
* [ ] `TaskCard` em `src/components` com props
* [ ] App continua adicionando/deletando normalmente
* [ ] Issue, branch `feature/pratica05`, commit, push e Pull Request

### Commit sugerido

```bash
git add .
git commit -m "Feat: Adiciona FlatList, AsyncStorage e componente TaskCard"
git push origin feature/pratica05
```

Parabéns: ao final desta trilha você saiu do zero (conceito + ambiente) até um To-Do multiplataforma com persistência e código organizado.
>>>>>>> 6e3395a (Atualizando as aulas)
