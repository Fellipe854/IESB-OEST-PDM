<<<<<<< HEAD
# 📚 Aula 02: Expo e a Anatomia de um Projeto

Na Aula 01 você entendeu o “porquê” do React Native. Agora vamos ao “como começar”: o papel do **Expo** no dia a dia e o significado de **cada arquivo** gerado quando criamos um projeto.

## 🎯 Objetivos da Aula

* Diferenciar React Native “puro” e projeto com Expo.
* Conhecer as ferramentas Expo (Go, CLI, SDK, Snack, EAS).
* Explicar a função de `package.json`, `App.js`, `app.json`, `node_modules`, etc.
* Entender `View` e `Text` como primeiros blocos de construção da UI.

---

## 🧰 Expo na prática

O Expo **não substitui** o React Native: ele **empacota** um projeto React Native com ferramentas que aceleram o desenvolvimento.

| Peça | Função no seu dia a dia |
| :--- | :--- |
| **Expo Go** | Instala no celular e espelha o app enquanto você programa |
| **Expo CLI** | Comandos como `npx expo start` |
| **Expo SDK** | Bibliotecas oficiais (câmera, storage, etc.) |
| **Snack** | Testar código no navegador sem setup local |
| **EAS** | Builds para lojas (assunto avançado) |

Fluxo típico desta disciplina:

1. Você edita o código no VS Code.
2. O Metro Bundler (via `expo start`) empacota o JavaScript.
3. O Expo Go no celular baixa esse pacote e mostra a UI nativa.

---

## 📂 Anatomia do projeto (o que é cada coisa)

Quando você cria um app com `create-expo-app`, aparecem vários arquivos. Não precisa decorar tudo de uma vez — precisa **saber onde olhar**.

### `package.json`

É o **manifesto** do projeto. Contém:

* Metadados: `name`, `version`, `description`, `author`, `license`
* **`dependencies`**: pacotes necessários para o app rodar
* **`devDependencies`**: pacotes só de desenvolvimento (lint, testes, etc.)
* **`scripts`**: atalhos (`npm start`, `npm test`, …)
* Às vezes `main` (arquivo de entrada), `engines` (versão do Node), etc.

### `package-lock.json`

Gerado pelo **npm**. “Trava” as versões exatas das dependências e subdependências para que todos na equipe (e o seu PC daqui a um mês) instalem **as mesmas versões**. Não edite à mão.

### `App.js` / `App.tsx`

É o **coração da interface** no início do curso: o componente raiz da aplicação. É aqui que você começa a montar telas com `View`, `Text`, etc.

> Em templates mais novos do Expo, a estrutura pode usar pastas como `app/` (roteamento por arquivos). O princípio é o mesmo: existe um ponto de entrada da UI que você edita.

### `index.js` (quando existir)

Ponto de registro/entrada que “liga” o JavaScript ao runtime do React Native / Expo. Em muitos templates Expo você quase não mexe nele no começo.

### `app.json` (ou `app.config.js`)

Configuração do app no ecossistema Expo, por exemplo:

* Nome e ícone
* Splash screen
* Orientação da tela
* Identificadores / permissões para Android e iOS
* Número de versão

### `assets/`

Recursos estáticos: imagens, ícones, fontes, splash.

### `node_modules/`

Pasta onde o npm **baixa** as dependências listadas no `package.json`. É grande, gerada automaticamente e **não deve** ir para o Git (fica no `.gitignore`).

### `.expo/`

Pasta gerada pelo Expo com metadados/cache locais. Também costuma ser ignorada pelo Git.

### `.gitignore`

Lista o que o Git **não versiona** (`node_modules`, `.expo`, arquivos sensíveis, etc.). Essencial para não poluir o repositório.

---

## 🧱 Primeiros componentes: `View` e `Text`

No mobile, layouts são árvores de componentes. Dois blocos fundamentais:

### `<View>`

* É o **container** (parecido com a ideia de uma `<div>` na web).
* Serve para agrupar e posicionar outros elementos.
* **Não** renderiza texto sozinho: texto vai em `<Text>`.
* Pode conter outras `View`s, imagens, botões, inputs, componentes seus.

### `<Text>`

* Qualquer texto visível na tela precisa estar dentro de `<Text>`.
* Diferente da web, você **não** pode soltar uma string solta dentro de uma `View`.

Exemplo mínimo:

```javascript
import { View, Text } from 'react-native';

export default function App() {
  return (
    <View>
      <Text>Bem-vindo ao React Native!</Text>
    </View>
  );
}
```

---

## 🗺️ Mapa mental: do arquivo à tela

```text
Você edita App.js
        ↓
Metro empacota o JS
        ↓
Expo Go recebe o pacote
        ↓
React Native mapeia <View>/<Text> → UI nativa
        ↓
Você vê o resultado no celular
```

---

## ✅ Checklist de compreensão

1. Para que serve o `package.json`?
2. Por que `node_modules` não vai para o Git?
3. O que configuramos no `app.json`?
4. Por que texto não pode ficar solto dentro de uma `View`?

Na **Prática 02**, você cria/organiza o projeto na pasta da prática, explora esses arquivos e personaliza a primeira tela com `View` e `Text`.
=======
# 📚 Aula 02: Fundamentos de Interface no React Native

Nesta aula, deixamos a web de lado (adeus HTML e CSS tradicional) e mergulhamos na forma nativa de construir interfaces. Vamos entender como o React Native traduz o nosso código JavaScript para elementos visuais reais no Android e no iOS.

## 🎯 Objetivos da Aula
* Compreender o mapeamento de tags Web (HTML) para Componentes Core do React Native.
* Entender o funcionamento do `StyleSheet`.
* Dominar o básico do **Flexbox** voltado para o ambiente mobile.

## 🧱 Componentes Core (O "HTML" do Mobile)
No React Native, não usamos `<div>`, `<h1>` ou `<input>`. Precisamos importar componentes específicos do pacote `react-native`:

| Web (ReactJS) | Mobile (React Native) | Para que serve? |
| :--- | :--- | :--- |
| `<div>` | `<View>` | Container principal para agrupar outros elementos. |
| `<p>`, `<h1>`, `<span>` | `<Text>` | Qualquer texto **precisa** estar dentro desta tag. |
| `<input type="text">` | `<TextInput>` | Campo para o usuário digitar. |
| `<button>` | `<TouchableOpacity>` | Botão customizável que pisca (muda opacidade) ao toque. |

## 🎨 Estilização (O "CSS" do Mobile)
Não temos arquivos `.css`. Toda a estilização é feita via JavaScript usando o `StyleSheet.create({})`. 
* As propriedades são escritas em `camelCase` (ex: `backgroundColor` em vez de `background-color`).
* Não usamos `px` (pixels). Os valores numéricos são unidades independentes de densidade. Ex: `fontSize: 16`.

## 📦 Flexbox no React Native
O Flexbox é a única forma de criar layouts no React Native. Ele funciona quase igual à web, mas com **uma diferença crucial**:
* Na Web, o padrão do Flexbox é colocar os itens em linha (`flexDirection: 'row'`).
* No Mobile, o padrão é colocar os itens em coluna (`flexDirection: 'column'`), um embaixo do outro, respeitando o formato da tela do celular.



**Propriedades mais usadas:**
* `justifyContent`: Alinha os itens no eixo principal (vertical por padrão).
* `alignItems`: Alinha os itens no eixo secundário (horizontal por padrão).
>>>>>>> 62a42f7 (Subindo o template para o repositório)
