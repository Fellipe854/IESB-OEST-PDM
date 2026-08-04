<<<<<<< HEAD
# 📚 Aula 05: Listas Eficientes e Persistência Local

Com o To-Do interativo, aparecem dois problemas típicos de app real:

1. Listas grandes com `.map()` pesam na performance e na rolagem.
2. Fechar o app **apaga** tudo (estado vive só na memória).

Nesta aula resolvemos isso com `FlatList`, AsyncStorage e `useEffect`. A organização do código em componentes fica para a **Aula 06**.

## 🎯 Objetivos da Aula

* Entender por que `.map()` não escala bem em listas longas no mobile.
* Usar `<FlatList>` para rolagem eficiente.
* Persistir dados com `@react-native-async-storage/async-storage`.
* Carregar dados na abertura do app com `useEffect`.

---

## 📜 Por que `FlatList`?

Na web, `.map()` é comum. No mobile, uma lista com centenas de itens tenta desenhar **tudo de uma vez** e pode travar a UI.

A `FlatList` usa virtualização: renderiza sob demanda, aproximadamente o que está visível na tela. Ao rolar, recicla itens que saíram da área visível.

### Props essenciais

| Prop | Função |
| :--- | :--- |
| `data={tasks}` | Array de origem |
| `keyExtractor={(item) => item.id}` | Identificador único de cada item |
| `renderItem={({ item }) => ...}` | Como desenhar cada linha |

```javascript
<FlatList
  data={tasks}
  keyExtractor={(item) => item.id}
  renderItem={({ item }) => (
    <View>
      <Text>{item.title}</Text>
      <TouchableOpacity onPress={() => handleDelete(item.id)}>
        <Text>X</Text>
      </TouchableOpacity>
    </View>
  )}
/>
```

Por enquanto o card pode continuar **dentro** do `renderItem` no `App.js`. Na próxima aula vamos extrair isso para um componente.

---

## 💾 AsyncStorage (persistência local)

`useState` mora na RAM: fechou o app, perdeu os dados.

O AsyncStorage funciona como um **gaveteiro chave → valor** no aparelho. Só grava **strings**.

* Salvar objeto/array: `JSON.stringify(...)`
* Ler de volta: `JSON.parse(...)`
* Operações são **assíncronas** (`async` / `await`)

Instalação no projeto Expo:

```bash
npx expo install @react-native-async-storage/async-storage
```

Ideia geral:

```javascript
await AsyncStorage.setItem('@tasks', JSON.stringify(tasks));

const raw = await AsyncStorage.getItem('@tasks');
const parsed = raw ? JSON.parse(raw) : [];
```

---

## ⏱️ `useEffect` — carregar ao abrir

Para buscar as tarefas salvas **quando a tela monta**:

```javascript
import { useEffect } from 'react';

useEffect(() => {
  loadTasks();
}, []); // [] = executar uma vez na montagem
```

Boas práticas neste exercício:

* `loadTasks` no `useEffect` com `[]`.
* `saveTasks` sempre que a lista mudar (após add e após delete), com a lista **já atualizada**.

---

## 🔁 Fluxo mental

```text
App abre → useEffect → loadTasks → setTasks → FlatList desenha
Usuário adiciona → setTasks → saveTasks → disco atualizado
Usuário fecha o app → RAM zera, disco mantém
App abre de novo → loadTasks restaura a lista
```

---

## ✅ Checklist de compreensão

1. Quais 3 props básicas a `FlatList` exige?
2. Por que AsyncStorage precisa de `JSON.stringify`?
3. O que o array `[]` no `useEffect` significa?
4. Quando chamar `saveTasks` neste exercício?

Na **Prática 05**, você troca `.map()` por `FlatList` e faz o app **lembrar** das tarefas após fechar.
=======
# 📚 Aula 05: Arquitetura, Componentização e Props

Neste ponto do campeonato, nosso arquivo `App.js` deve estar enorme. Temos funções de armazenamento, lógica de estado e várias tags de interface misturadas. Hoje, vamos aprender a pensar como engenheiros de software e organizar nosso projeto em "blocos de montar" (Lego).

## 🎯 Objetivos da Aula
* Entender o conceito de **Componentização**.
* Aprender a estruturar pastas em um projeto real (`src/components`).
* Dominar o uso de **Props** (Propriedades) para passar dados de um arquivo para outro.

## 🧱 O que é Componentização?
No React, um Componente é basicamente uma função JavaScript que retorna uma interface (UI). Em vez de termos um arquivo gigante com 500 linhas de código, nós quebramos a interface em pedaços menores, reutilizáveis e independentes.

* **Exemplo:** Em vez de desenhar a caixa de texto e o botão de "+" direto no `App.js`, criamos um arquivo separado chamado `InputTarefa.js`.
* **Vantagem:** Se houver um bug no botão de adicionar, você sabe exatamente em qual arquivo procurar, sem correr o risco de quebrar a lista de tarefas.

## 🤝 Props (Propriedades): A Comunicação entre Arquivos
Quando quebramos o app em vários arquivos, surge um problema: o Estado (`tasks`) está no `App.js`, mas o botão de deletar agora está dentro do arquivo `CardTarefa.js`. Como um fala com o outro? Através das **Props**.

As Props são como "parâmetros de função" no mundo do React. Elas permitem que o Componente Pai (`App.js`) envie dados ou funções para o Componente Filho (`CardTarefa.js`).

**Exemplo no Componente Pai (`App.js`):**
```javascript
// Enviando o texto da tarefa e a função de deletar como Props
<CardTarefa titulo="Estudar React" aoDeletar={funcaoDeletar} />
```
**Exemplo no Componente Filho (`CardTarefa.js`):**
```javascript
// Recebendo as Props (usamos desestruturação {})
export function CardTarefa({ titulo, aoDeletar }) {
  return (
    <View>
      <Text>{titulo}</Text>
      <TouchableOpacity onPress={aoDeletar}>
         <Text>X</Text>
      </TouchableOpacity>
    </View>
  );
}
```
📂 **Estrutura de Pastas Padrão**
No mercado, não deixamos os arquivos soltos na raiz. Criamos uma pasta src/ (Source) e organizamos por responsabilidade:
- src/components/: Pedaços de tela (Botões, Cards, Inputs).
- src/screens/: Telas inteiras (Tela Home, Tela de Login).
- src/services/: Conexões com banco de dados ou APIs.
>>>>>>> 62a42f7 (Subindo o template para o repositório)
