<<<<<<< HEAD
# 📚 Aula 04: Estado, Interatividade e Imutabilidade

Na aula anterior a tela *parece* um app de tarefas, mas digitar e tocar no botão **não muda nada de verdade**. Interfaces React são declarativas: elas mostram o que está no **estado**. Sem estado, a UI é só um desenho estático.

## 🎯 Objetivos da Aula

* Diferenciar variável comum de estado (`useState`).
* Entender re-renderização: por que a tela atualiza.
* Capturar texto do usuário com `TextInput` controlado.
* Aplicar a regra da **imutabilidade** em listas.

---

## 🧠 O problema da variável comum

```javascript
let nome = 'Maria';
nome = 'João'; // a variável muda, a tela NÃO
```

O React Native **não fica olhando** variáveis soltas. Ele só redesenha a interface quando um **estado** muda por meio da função setter.

---

## 🎣 Hook `useState`

```javascript
import { useState } from 'react';

const [taskText, setTaskText] = useState('');
const [tasks, setTasks] = useState([]);
```

| Parte | Significado |
| :--- | :--- |
| `taskText` | Valor atual (o que está digitado) |
| `setTaskText` | Função que atualiza o valor **e** pede novo desenho da tela |
| `useState('')` | Valor inicial |

### Input controlado

Ligue o campo ao estado:

```javascript
<TextInput
  value={taskText}
  onChangeText={setTaskText}
  placeholder="Digite uma tarefa..."
/>
```

Agora o que aparece no campo **é** o estado — e o estado reflete o que o usuário digita.

---

## ➕ Adicionar itens em uma lista

Cada tarefa deve ser um objeto com identificação única, por exemplo:

```javascript
{
  id: Date.now().toString(),
  title: 'Estudar React Native',
}
```

Para adicionar **sem mutar** o array antigo:

```javascript
const handleAdd = () => {
  if (taskText.trim() === '') return;

  const newTask = {
    id: Date.now().toString(),
    title: taskText.trim(),
  };

  setTasks([...tasks, newTask]); // nova lista = cópia + item novo
  setTaskText(''); // limpa o campo
};
```

O operador spread (`...`) cria um **novo** array. Isso é essencial para o React perceber a mudança.

---

## 🛡️ Regra de ouro: imutabilidade

**Nunca altere o estado diretamente.** Substitua por um valor novo.

```javascript
// ❌ ERRADO — mutação; a tela pode não atualizar
tasks.push(newTask);

// ✅ CERTO — novo array
setTasks([...tasks, newTask]);

// ✅ Remover pelo id — novo array filtrado
setTasks(tasks.filter((item) => item.id !== idClicked));
```

### Por que `.filter` para deletar?

`filter` devolve um **array novo** só com os itens que passam no teste. Ideal para “remover” sem `splice` no array original.

---

## 🖼️ Renderizar a lista com `.map()`

Enquanto a lista for pequena, podemos fazer:

```javascript
{tasks.map((item) => (
  <View key={item.id}>
    <Text>{item.title}</Text>
    <TouchableOpacity onPress={() => handleDelete(item.id)}>
      <Text>X</Text>
    </TouchableOpacity>
  </View>
))}
```

* `key` ajuda o React a identificar cada item.
* Se a lista crescer muito, a rolagem/performance sofrem — na próxima aula entra a `FlatList`.

---

## 🔁 Ciclo mental da interatividade

```text
Usuário digita → onChangeText → setTaskText → tela redesenha o input
Usuário toca + → handleAdd → setTasks([...]) → tela redesenha a lista
Usuário toca X → handleDelete → setTasks(filter) → item some da tela
```

---

## ✅ Checklist de compreensão

1. Por que `let x = 1` não atualiza a UI?
2. O que `setTasks` faz além de guardar o valor?
3. Por que `push` no array de estado é problema?
4. Como ligar `TextInput` ao estado?

Na **Prática 04**, você conecta a UI da Prática 03 a essa lógica: adicionar e deletar tarefas de verdade.
=======
# 📚 Aula 04: Listas Eficientes e Persistência Local

Na última aula, você deve ter notado um problema grave: quando adicionamos muitas tarefas, a tela não rola para baixo! Além disso, se fecharmos o aplicativo, todas as nossas tarefas somem. Hoje, vamos resolver esses dois problemas.

## 🎯 Objetivos da Aula
* Entender por que não devemos usar `.map()` para listas grandes no mobile.
* Aprender a usar o componente `<FlatList>` para rolagem eficiente.
* Compreender o funcionamento do `AsyncStorage` para salvar dados no celular.
* Introdução rápida ao ciclo de vida com `useEffect`.

## 📜 O Problema do `.map()` e a Solução: `FlatList`
Na Web, usamos o `.map()` o tempo todo. No mobile, se você tiver uma lista com 1000 itens, o `.map()` tentará desenhar os 1000 de uma vez, travando o celular do usuário.

A solução do React Native é a **`FlatList`**. Ela é inteligente: só desenha na tela os itens que o usuário está vendo no momento. Conforme ele rola para baixo, ela recicla a memória dos itens que ficaram para cima.

**Como usar a FlatList? Ela exige 3 propriedades (props) obrigatórias:**
1. `data={array}`: Qual é a lista de dados que ela vai renderizar?
2. `keyExtractor={(item) => item.id}`: Como ela identifica cada item de forma única?
3. `renderItem={({ item }) => <Card />}`: Como ela deve desenhar cada item na tela?

## 💾 Persistência de Dados (AsyncStorage)
O estado (`useState`) vive apenas na memória RAM. Fechou o app, a RAM é limpa. Para salvar de verdade no aparelho (como o WhatsApp salva suas conversas offline), usamos o `@react-native-async-storage/async-storage`.

Ele funciona como um "gaveteiro" de chave e valor (Key-Value), mas **só aceita textos (Strings)**.
* Para salvar um Array/Objeto, precisamos transformá-lo em texto usando `JSON.stringify()`.
* Para ler o texto e transformá-lo de volta em Array, usamos `JSON.parse()`.

Como ler e gravar no celular demora alguns milissegundos, essas funções são **Assíncronas** (precisamos usar `async` e `await`).

## ⏱️ O Gancho `useEffect`
Como fazemos para carregar as tarefas salvas exatamente no momento em que o app abre? Usamos o `useEffect`. Ele é um Hook que executa uma função num momento específico do ciclo de vida do componente.

```javascript
useEffect(() => {
  // O que colocar aqui dentro vai rodar assim que a tela abrir!
  carregarTarefas();
}, []); // O array vazio [] significa "rode apenas uma vez, na montagem".
```
>>>>>>> 62a42f7 (Subindo o template para o repositório)
