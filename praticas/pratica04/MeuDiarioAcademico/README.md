# MeuDiarioAcademico

Atividade 01 — Fundamentos de UI, Componentes e Layout
Disciplina: Programação para Dispositivos Móveis (React Native / Expo)
Professor: Marcelo Alves Farias — IESB

## Comando usado para criar o projeto

```bash
npx create-expo-app@latest MeuDiarioAcademico --template blank
```

Dependência extra instalada (SafeAreaView atualizado):

```bash
npx expo install react-native-safe-area-context
```

## Como rodar

```bash
cd MeuDiarioAcademico
npx expo start
```

Abra no emulador Android ou escaneando o QR code no app Expo Go.

## O que foi implementado

- **`labels.js`**: arquivo separado exportando as constantes de texto usadas
  na tela (título do app, placeholder do input, texto do botão, título da
  lista, texto do switch). Importado em `App.js`.
- **Layout (`App.js`)**:
  - `SafeAreaView` (de `react-native-safe-area-context`) envolvendo toda a tela.
  - Cabeçalho com o título do app.
  - Linha (`flexDirection: 'row'`) com `TextInput` (~68% de largura) e um
    botão (`Pressable`, ocupando o restante via `flex: 1`).
  - Lista estática de disciplinas, renderizada com `.map`.
- **Estilos** organizados com `StyleSheet.create`, incluindo `container`
  (`flex: 1` + padding), `input` (borda/raio), `item` da lista
  (margin/padding/backgroundColor), com comentários no código explicando o
  uso de `justifyContent` e `alignItems`.
- **Dimensões**: uso de largura percentual (`width: '68%'` no input) e uso
  de `flex` (no botão e na lista).
- **Desafio opcional**: `Button` substituído por `Pressable` com estilo de
  "pressionado", e `Switch` "Mostrar apenas obrigatórias" (ainda sem lógica
  de filtro).

## Prints da tela

> Substitua esta seção pelos prints reais da tela rodando no emulador/Expo Go
> antes de entregar (arraste as imagens para este README ou anexe na pasta
> `assets/` e referencie aqui).

```
[ colar print da tela aqui ]
```

## Estrutura do projeto

```
MeuDiarioAcademico/
├── App.js
├── labels.js
├── app.json
├── babel.config.js
├── package.json
├── .gitignore
└── assets/
```

> Observação: `node_modules/` não está incluído neste pacote, conforme
> pedido no enunciado. Rode `npm install` (ou `npx expo install`) após
> extrair o projeto.
