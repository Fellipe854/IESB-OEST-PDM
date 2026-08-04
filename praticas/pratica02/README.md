<<<<<<< HEAD
# 💻 Prática 02: Criar o Projeto e Explorar a Estrutura

Agora você vai **criar o projeto Expo desta prática**, abrir os arquivos gerados e provar que entendeu a anatomia do app — alterando a tela com `View` e `Text` de forma consciente.

## 🎯 Objetivos

* Criar um projeto Expo dentro de `praticas/pratica02`.
* Identificar a função dos principais arquivos/pastas.
* Montar uma tela simples e organizada com `View` e `Text`.
* Seguir o fluxo Git (Issue → Branch → PR).

---

## 📦 Parte A — Fluxo Git

1. Crie a Issue da **Prática 02**.
2. A partir da branch principal:

```bash
git checkout -b feature/pratica02
```

3. Entre na pasta da prática:

```bash
cd praticas/pratica02
```

---

## 🚀 Parte B — Criar o projeto Expo

Na pasta `praticas/pratica02`:

```bash
npx create-expo-app@latest .
```

Se a pasta não estiver vazia por causa do README, use uma subpasta:

```bash
npx create-expo-app@latest todo-basico
cd todo-basico
```

Instale e rode:

```bash
npm install
npx expo start
```

Abra no **Expo Go** e confirme que o app template carrega.

---

## 🔍 Parte C — Atividade guiada: “o que é cada arquivo?”

Abra o projeto no VS Code e, no próprio README desta prática (ou em um arquivo `ESTRUTURA.md` na pasta do app), escreva **em uma frase** o papel de cada item abaixo (use a Aula 02 como referência):

* [ ] `package.json`
* [ ] `package-lock.json`
* [ ] `App.js` / `App.tsx` (ou pasta `app/`, se o template usar)
* [ ] `app.json`
* [ ] `assets/`
* [ ] `node_modules/`
* [ ] `.gitignore`
* [ ] `.expo/` (se aparecer após rodar o Expo)

> Dica: se tiver dúvida, busque na documentação Expo/React Native — o exercício da aula de slides pedia exatamente isso: pesquisar a função de cada arquivo gerado.

---

## ✏️ Parte D — Tela “Bem-vindo”

No arquivo principal da UI:

1. Importe `View` e `Text` de `react-native`.
2. Remova o conteúdo padrão desnecessário.
3. Monte uma tela com:
   * Um título: `Programação para Dispositivos Móveis`
   * Um subtítulo: `Olá, [Seu Nome]!`
   * Uma linha de apoio: `Meu segundo passo com Expo e React Native`

Estrutura sugerida (você pode melhorar):

```javascript
import { View, Text } from 'react-native';

export default function App() {
  return (
    <View>
      <Text>Programação para Dispositivos Móveis</Text>
      <Text>Olá, [Seu Nome]!</Text>
      <Text>Meu segundo passo com Expo e React Native</Text>
    </View>
  );
}
```

4. (Opcional) Altere o **nome do app** em `app.json` para algo como `pdm-pratica02`.

Ainda **não** é obrigatório dominar `StyleSheet` — se quiser, use apenas propriedades simples (`fontSize`, `padding`) para legibilidade. Estilo e Flexbox entram com força na próxima aula.

---

## ✅ Critérios de entrega

* [ ] Projeto Expo criado e rodando no Expo Go
* [ ] Anotações curtas sobre a função dos arquivos principais
* [ ] Tela com título da disciplina + seu nome
* [ ] Issue, branch `feature/pratica02`, commit, push e Pull Request

### Commit sugerido

```bash
git add .
git commit -m "Feat: Cria projeto Expo e explora estrutura com tela de boas-vindas"
git push origin feature/pratica02
```

Na **Aula 03**, vamos explorar os **componentes core**, o `StyleSheet` e o **Flexbox** — a base visual do nosso To-Do List.
=======
# 💻 Prática 02: Construindo a Interface da Lista de Tarefas

Chegou a hora de dar uma "cara" ao nosso aplicativo! Nesta prática, vamos construir a **Interface Gráfica (UI)** do To-Do List. Ainda não teremos funcionalidades reais (como adicionar ou deletar), o objetivo hoje é apenas desenhar a tela usando os Componentes Core e o StyleSheet.

## 🛠️ O que deve ser feito

1. **Siga o Fluxo:** Crie a Issue da Prática 02 no GitHub, depois crie a branch `feature/pratica02` no seu terminal.
2. Limpe o arquivo `App.js` (ou `App.jsx`) removendo o "Hello World" da aula passada.
3. Construa a seguinte estrutura visual:
   * **Cabeçalho:** Um título grande e em negrito escrito "Minhas Tarefas".
   * **Área de Inserção:** Um `<TextInput>` para digitar a tarefa e, ao lado dele, um botão (`<TouchableOpacity>`) com um ícone de `+` ou o texto "Add". Use Flexbox (`flexDirection: 'row'`) para deixá-los na mesma linha.
   * **Lista de Tarefas (Estática):** Crie 2 ou 3 "cards" de tarefas fixos no código (hardcoded). Cada card deve ter um texto longo e um botão de lixeira (pode ser apenas um texto "X" por enquanto).

## 💡 Dicas de Estilização
Abaixo está um "esqueleto" mental de como seu código deve se parecer. Tente usar essas propriedades no seu `StyleSheet`:

* Use `padding` na `View` principal para desgrudar os elementos das bordas do celular.
* No `TextInput`, use `borderWidth`, `borderColor` e `borderRadius` para criar a caixa de texto.
* Lembre-se: Para colocar o Input e o Botão lado a lado, coloque os dois dentro de uma `<View>` e aplique `flexDirection: 'row'` nessa View!

## ✅ Como Entregar
1. Verifique se o layout ficou agradável no seu celular via Expo Go.
2. Faça o commit: `git commit -m "Feat: Cria interface estatica do app de tarefas"`
3. Faça o push para o GitHub e abra o seu **Pull Request** para correção!
>>>>>>> 62a42f7 (Subindo o template para o repositório)
