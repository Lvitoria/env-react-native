# Configuração das Variáveis de Ambiente no React Native

Este é um guia para configurar e utilizar variáveis de ambiente no seu projeto React Native.

## Pré-requisitos

Certifique-se de ter o ambiente de desenvolvimento do React Native configurado e funcionando corretamente.

## Passo 1: Instalação das Dependências

1. No diretório raiz do seu projeto React Native, instale a biblioteca `react-native-dotenv`:
```shell
npm install react-native-dotenv --save-dev
```

2. No diretório raiz do seu projeto, crie um arquivo chamado .env e defina suas variáveis de ambiente nele.

3. altere o arquivo chamado `babel.config.js` no diretório raiz do seu projeto e adicione o seguinte conteúdo:

```json
{
   "plugins": [
      [
        "module:react-native-dotenv",
        {
          "moduleName": "@env",
          "path": ".env",
          "blacklist": null,
          "whitelist": null,
          "safe": false,
          "allowUndefined": true,
        },
      ],
    ]
}

```

4. Depois para usar a env dentro do codigo basta chama-lo com `'@env'`

```javascript
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';
import { API_URL, API_KEY } from '@env';

export default function App() {
  console.log(API_URL);
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
      <Text>API URL: {API_URL}</Text>
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});

```