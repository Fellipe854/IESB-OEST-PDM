<<<<<<< HEAD
# 💻 Prática 04: Dando Vida ao App (Adicionar e Deletar)

Vamos conectar a interface ao React. Ao final, você digita uma tarefa, adiciona à lista e remove pelo `X`.

## 🎯 Objetivos

* Criar estados para o texto do input e para a lista.
* Implementar `handleAdd` e `handleDelete` com imutabilidade.
* Trocar cards estáticos por renderização com `.map()`.
* Validar o fluxo no Expo Go.

---

## 📦 Fluxo Git

1. Crie a Issue da **Prática 04**.
2. Branch:

```bash
git checkout -b feature/pratica04
```

3. Continue o app em `praticas/pratica04` (crie o Expo se ainda não existir, ou evolua a cópia da Prática 03).

```bash
npm install
npx expo start
```

---

## 🛠️ O que implementar

### 1. Estados

No componente principal:

* `taskText` — string do que está sendo digitado (`useState('')`)
* `tasks` — array de tarefas (`useState([])`)

### 2. Capturar digitação

No `TextInput`:

* `value={taskText}`
* `onChangeText={setTaskText}`

### 3. Função `handleAdd`

* Ignore texto vazio (`trim`).
* Crie objeto `{ id, title }` (`id` com `Date.now().toString()` é suficiente neste exercício).
* Atualize a lista com spread: `setTasks([...tasks, newTask])`.
* Limpe o input: `setTaskText('')`.
* Ligue essa função no `onPress` do botão `+`.

### 4. Renderizar com `.map()`

* Remova os cards hardcoded.
* Use `tasks.map(...)` para desenhar cada card.
* Não esqueça a prop `key={item.id}`.

### 5. Função `handleDelete(id)`

* Use `filter` para gerar nova lista sem o id clicado.
* Passe a função ao `onPress` do `X` de cada card.

---

## 🧪 Como testar

1. Adicione 3 tarefas diferentes.
2. Delete a do meio.
3. Confirme que o input limpa após adicionar.
4. (Esperado) Com muitas tarefas, a tela **pode não rolar bem** — isso será resolvido na próxima aula com `FlatList`.

---

## ✅ Critérios de entrega

* [ ] Adicionar e deletar funcionando no celular
* [ ] Estados + imutabilidade (sem `push`/`splice` no estado)
* [ ] Lista renderizada com `.map()`
* [ ] Issue, branch `feature/pratica04`, commit, push e Pull Request

### Commit sugerido

```bash
git add .
git commit -m "Feat: Implementa useState para adicionar e remover tarefas"
git push origin feature/pratica04
```

Na **Aula 05**, vamos melhorar listas (`FlatList`) e persistir dados no aparelho (`AsyncStorage`). A organização em componentes fica para a Aula 06.
=======
# 💻 Prática 04: Rolagem Infinita e App que Não Esquece

Nesta prática, vamos melhorar a usabilidade do nosso App de Tarefas. Vamos substituir a nossa lista rudimentar por uma lista nativa de alta performance e conectar o nosso aplicativo ao armazenamento interno do celular.

## 🛠️ O que deve ser feito

1. **Siga o Fluxo:** Crie a Issue da Prática 04, crie a branch `feature/pratica04` e rode o projeto (`npx expo start`).
2. **Refatoração para FlatList:** * Remova o `.map()` que você usou na prática passada.
   * Importe o componente `<FlatList>` do `react-native`.
   * Configure a `FlatList` passando o seu estado `tasks` para a prop `data`.
   * Passe a função que desenha o seu card de tarefa para a prop `renderItem`. Teste adicionando 15 tarefas e veja a mágica da rolagem acontecer!
3. **Instale o AsyncStorage:** Pare o servidor no terminal (Ctrl+C) e rode o comando:
   ```bash
   npx expo install @react-native-async-storage/async-storage
   ```
4. **Crie a Função de Salvar:**
- Crie uma função assíncrona chamada `saveTasks()`.
- Toda vez que você adicionar ou deletar uma tarefa, chame o `AsyncStorage.setItem()` para guardar a nova lista atualizada (não esqueça de usar `JSON.stringify`).

5. **Crie a Função de Carregar:**
- Crie uma função assíncrona chamada `loadTasks()`.
- Use o `AsyncStorage.getItem()` para buscar as tarefas salvas. Se existirem, use o `JSON.parse` e coloque-as no seu estado usando o `setTasks()`.

6. **O Toque Final (useEffect):**
- Importe o `useEffect` do `react`.
- Configure o `useEffect` com um array de dependências vazio `[]` para chamar a função loadTasks() assim que o aplicativo for aberto.

✅ **Como Entregar**
- **Teste Extremo:** Abra o seu aplicativo no celular, adicione 3 tarefas. Feche o aplicativo completamente (remova da lista de apps recentes) e abra de novo. As tarefas precisam continuar lá!
- Faça o commit: `git commit -m "Feat: Adiciona FlatList e AsyncStorage para persistir tarefas"`
- Faça o push para o GitHub e abra o seu **Pull Request** para a revisão!
>>>>>>> 62a42f7 (Subindo o template para o repositório)
