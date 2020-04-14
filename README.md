# Dia 06 - Mobile com React Native

Data: Apr 13, 2020
Hora de inГ­cio: 19:15
Status: Iniciado

Hoje vou inciar os estudo de React Native

## Aulas

- [x] Arquitetura React Native
- [x] Configurando SDK
- [x] Criando Novo Projeto
- [x] diferenças do ReactJS
- [x] Listando Projetos da API
- [x] Criando novos projetos

# Arquitetura React Native

## O que é React Native ?

- VersГЈo do React para desenvolvimento mobile;
  - React cuida de desenvolvimento de interfaces (TV/Mobile/Plataforma).
- Multiplataforma;
- Podemos manipular cada plataforma de forma diferente;
- interface nativa ou hГ­brida ?
  - não produz interface hГ­brida;
  - Ele converte o código em interface nativa;
- código não é transpilado;
  - O código não é totalmente convertido;
  - Ele Injeta o JavascriptCore em nosso dispositivo, e assim faz com que ele entenda Javascript(JSX).
- Outras Plataformas migrando, Microsoft com Windows(+40 aplicaГ§Гµes);

## Arquitetura

Tudo comeГ§a com o código Javascript, ele passa por uma ferramenta chamada Metro Bundler, o papel dele é monitorar todo o nosso código, e gerar um arquivo chamado `bundle`, o código dentro arquivo `bundle`, é passo pela Bridge, que é a ponte de comunicaГ§ГЈo entre o código Javascript e o código Nativo, depois da Bridge, ele transforma o código compatГ­vel, tanto para Android(Java), quanto para IOS(Objective C).

## Sintaxe

```jsx
import { StyleSheet, View, Text, TouchbleOpacity } from "react-native";

function Button() {
  return (
    <View style={styles.container}>
      <TouchbleOpacity style={styles.button}>
        <Text style={styles.text}>Enviar</Text>
      </TouchbleOpacity>
    </View>
  );
}
```

```jsx
const styles = StyleSheet.create({
  container: {
    alignItems: "center",
  },
  button: {
    backgroundColor: "#7159c1",
  },
  text: {
    fontWeight: "bold",
  },
});
```

- A declaraГ§ГЈo de componentes é igual ao web;
- não usamos HTML e sim componentes prГіprios;
- Aplicamos o estilo sem classes ou ID's;
- Todo texto é `<Text/>`não existe estilizaГ§ГЈo prГіrpria
  - Tudo deve ser estilizado do zero;

## O que é Expo? Vamos usar ?

- SDK com conjunto de funcionalidade prontas para usar (cГўmera, vГ­deo, IntegraГ§ГЈo com diversos serviГ§os sejam ele: Meios de pagamento, GeolocalizaГ§ГЈo, Login com Facebook | Google e etc...);
- não é necessГЎrio configurar emulador;

### Porque não vamos utilizar ?

- LimitaГ§ГЈo sobre o controle do código nativo;
  - Ou seja, não podemos mexer de fato no código nativo da aplicaГ§ГЈo, o Expo não nos permite;
- VГЎrias bibliotecas não tem suporte para o Expo;
- O Expo liberou seu conjunto de ferramentas prontas para serem utilizadas com projetos que não utilizam Expo;

---

# Configurando SDK

Configurando ambiente de desenvolvimento;

Acesse este l[ink](https://react-native.rocketseat.dev) e siga o tutorial para a sua plataforma.

---

# Criando Novo Projeto

Inicialize um novo projeto com o comando abaixo:

    react-native init nome-do-projeto

Estrutura do projeto:

```
├── __tests__
│   └── App-test.js
├── android/
├── ios/
├── node_modules/
├── .buckconfig
├── .eslintrc.js
├── .flowconfig
├── .gitattributes
├── .gitignore
├── .prettierrc.js
├── .watchmanconfig
├── App.js
├── app.json
├── babel.config.js
├── index.js
├── metro.config.js
├── package.json
└── yarn.lock
```

Essa é a estrutura, que é bem parecida com a do ReactJS, porem alguma pastas diferentes, a pasta android/ e a pasta ios/ .

Para executar o projeto, rode o comando abaixo:

    yarn android

Depois de buildar a aplicaГ§ГЈo, e instalar no seu emulador/dispositivo execute o comando abaixo para startar o `react-native`.

    yarn start

Agora na raiz do projeto, apague o arquivo `App.js`, crie uma pasta com o nome `src` e dentro dessa pasta crie um arquivo `index.js` e deixe-o dessa maneira:

```jsx
import React from "react";
import { View, Text } from "react-native";

export default function App() {
  return (
    <View>
      <Text>Hello World</Text>
    </View>
  );
}
```

Agora vamos editar o arquivo `index.js` da raiz do projeto, mude somente a importaГ§ГЈo do `App.js`:

```jsx
import { AppRegistry } from "react-native";
import App from "./src"; // aqui :)
import { name as appName } from "./app.json";

AppRegistry.registerComponent(appName, () => App);
```

E fim, temos o nosso Hello World em Tela!!

---

# Diferença do ReactJS

Existem 2 principais diferenças

- Elementos
  - No React Native não utilizamos HTML (`div`, `p`, `span`, `small`, `header` e etc...);
  - Temos que utilizar elementos que sГЈo exportados diretamente do React Native (`View`, `Text`, `FlatList` e etc...);
  - A `View`, pode ser utilizada como: `div`, `footer`, `header`, `main`, `aside`, `section` e etc...
  - O `Text`, pode ser utilizado como: `p`, `span`, `strong`, `h1`, `h2`, `h3` e etc...
  - Os elementos no React Native não tem significado semГўntico, ou seja não possui significado.
- EstilizaГ§ГЈo

  - Todos os componentes não possuem estilizaГ§ГЈo prГіpria
  - Para estilizar importamos o `StyleSheet` de dentro do prГіprio React Native;
  - As propriedades sГЈo as mesmas do CSS tradicional, porem, não utilizamos o hГ­fen (`-`) para especificar propriedades usamos o `camelCase`, Ex: de `background-color` в†’ `backgroundColor`.
  - Para estilizar algum elemento siga o exemplo a seguir:

```jsx
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
  },
});
```

- Para aplicar o estilo acima, siga o exemplo abaixo:

```jsx
import React from "react";
import { View, Text, StyleSheet } from "react-native";
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
  },
});
export default function App() {
  return (
    <View style={styles.container}>
      <Text>Hello World</Text>
    </View>
  );
}
```

O resultado é esse:

  <img src="https://i.imgur.com/zgJV9rm.jpg" width="200" height="400"/>

    - Todos os elementos do React Native possuem por padrГЈo `display: flex;`.
    - O React Native não possui heranГ§a, ou seja temos que estilizar elemento por elemento.
    - Agora vamos estilizar o texto, colocando ele um pouco maior, de uma cor diferente, e no centro da tela:

```jsx
import React from "react";
import { View, Text, StyleSheet } from "react-native";
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  title: {
    color: "#fff",
    fontSize: 20,
    fontWeight: "bold",
  },
});
export default function App() {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Hello World</Text>
    </View>
  );
}
```

O cóіdigo é bem simples e o resultado é esse:

  <img src="https://i.imgur.com/jZXdhub.jpg" width="200" height="400"/>

- Pra finalizar, vamos personalizar a `StatusBar`, importando ela da lib do React Native como um componente, siga o exemplo abaixo:

```jsx
import React from "react";
import { View, Text, StyleSheet, StatusBar } from "react-native";
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  title: {
    color: "#fff",
    fontSize: 20,
    fontWeight: "bold",
  },
});
export default function App() {
  return (
    <>
      <StatusBar barStyle="light-content" backgroundColor="#7159c1" />
      <View style={styles.container}>
        <Text style={styles.title}>Hello World</Text>
      </View>
    </>
  );
}
```

Importamos o componente `StatusBar`, e definimos a cor do conteГєdo, e a sua cor de fundo, e o resultado é o seguinte:

  <img src="https://i.imgur.com/jfCpeF5.jpg" width="200" height="400"/>

A `StatusBar`, da cor da nossa aplicaГ§ГЈo!

---

# Listando projetos da API

Acesse a pasta do [back-end](https://github.com/DanPHP7/01-aula-conceitos-nodejs) e inicie a aplicação, para poder ser consumida pela nossa aplicaГ§ГЈo React Native!

Agora vamos consumir a `**api**` criada no mГіdulo de **back-end** com **nodejs**, para consumir a `**api**` é necessГЎrio instalarmos uma dependГЄncia para fazer chamadas a nossa `**api**`, essa dependencia se chama **`axios`**, para instalar basta executar o seguinte comando no terminal:

    yarn add axios

Agora vamos criar uma pasta chamada `services`, dentro da pasta `src`, e dentro dessa pasta `services` vamos criar o arquivo `**api.js**`, é dentro desse arquivo que vai a configuraГ§ГЈo da base da nossa `**api**`, agora edite esse arquivo **`api.js`**, e deixe-o da seguinte forma:

```jsx
import axios from "axios";

const api = axios.create({
  baseURL: "http://192.168.3.150:3333",
});

export default api;
```

Aqui nessa parte temos algumas peculiaridades quanto a **`baseURL`**, caso vocГЄ:

- Esteja utilizando **iOS** com emulador: `localhost`;
- Esteja utilizando **iOS** com dispositivo fГ­sico: `IP` da mГЎquina na rede;
- Esteja utilizando **Android** com emulador: `localhost` (`**adb reverse**`);
- Esteja utilizando **Android** com emulador: `10.0.2.2` (Android Studio);
- Esteja utilizando **Android** com emulador: `10.0.3.2` (Genymotion);
- Esteja utilizando **Android** com dispositivo fГ­sico: `IP` da mГЎquina na rede;

Essas são as opções que temos pra fazer a conexão do nosso dispositivo com o nosso `localhost`.

Agora voltando ao `src/index.js`, importamos a `**api**`, e vamos fazer o mesmo processo feito no [projeto web](https://www.notion.so/Dia-04-Front-End-com-Reactjs-Guia-B-sico-de-Reactjs-b47b3be98b2246d08db740f72b5503f2), siga o código abaixo para fazer a listagem dos `projects` com a nossa `**api**`.

```jsx
import React, { useEffect, useState } from "react";
import { View, Text, StyleSheet, StatusBar } from "react-native";
import api from "./services/api"; // importando api

export default function App() {
  const [projects, setProjects] = useState([]); // criando o estado

  useEffect(() => {
    api.get("/projects").then((response) => setProjects(response.data));
  }, []);

  return (
    <>
      <StatusBar barStyle="light-content" backgroundColor="#7159c1" />
      <View style={styles.container}>
        {/**Fazendo a iteração**/}
        {projects.map((project) => (
          <Text style={styles.project} key={project.id}>
            {project.title}
          </Text>
        ))}
      </View>
    </>
  );
}
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  // mudanГ§a no estilo
  project: {
    color: "#fff",
    fontSize: 20,
  },
});
```

O resultado deve ser igual á esse:

<img src="https://i.imgur.com/a5c2IWR.jpg" width="200" height="400"/>

O problema de fazermos dessa forma é que quando temos uma iteração muito grande, nГіs não teremos o `scroll` da lista, existem 2 formas de fazer o `scroll`, a primeira é importando o componente `**ScrollView**`, e substituirmos no lugar da `**View**` que encapsula nossa iteração, fazendo isso, temos o seguinte código:

```jsx
import React, { useEffect, useState } from "react";
import {
  View,
  Text,
  StyleSheet,
  StatusBar,
  ScrollView, // importando a ScrollView
} from "react-native";
import api from "./services/api";

export default function App() {
  const [projects, setProjects] = useState([]);

  useEffect(() => {
    api.get("/projects").then((response) => setProjects(response.data));
  }, []);

  return (
    <>
      <StatusBar barStyle="light-content" backgroundColor="#7159c1" />
      {/** E subsituimos onde nos usavamos a View*/}
      <ScrollView style={styles.container}>
        {projects.map((project) => (
          <Text style={styles.project} key={project.id}>
            {project.title}
          </Text>
        ))}
      </ScrollView>
    </>
  );
}
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    // justifyContent: "center", porem temos que comentar essas 2 propriedades
    // alignItems: "center",
  },
  project: {
    color: "#fff",
    fontSize: 120, // aumentamos a fonte pra ver o efeito
  },
});
```

Ele vai apresentar o seguinte efeito:

  <img src="https://i.imgur.com/VJQXrnz.gif" width="200" height="400"/>

Não é o efeito mais performático, entãoo vamos melhorar esse cóіdigo utilizando a `FlatList`, esse é um componente que foi especialmente criado pra lidar com listas dentro do React Native, para otermos o resultado anterior, vamos importar o FlatList e aplicar seus conceitos:

```jsx
import React, { useEffect, useState } from "react";
import {
  View,
  Text,
  StyleSheet,
  StatusBar,
  FlatList, // importando
} from "react-native";
import api from "./services/api";

export default function App() {
  const [projects, setProjects] = useState([]);

  useEffect(() => {
    api.get("/projects").then((response) => setProjects(response.data));
  }, []);

  return (
    <>
      <StatusBar barStyle="light-content" backgroundColor="#7159c1" />
      <FlatList
        style={styles.container}
        data={projects}
        keyExtractor={(project) => project.id}
        renderItem={({ item: project }) => (
          <Text style={styles.project}>{project.title}</Text>
        )}
      />
      {/* <View style={styles.container}>
            {projects.map((project) => (
              <Text style={styles.project} key={project.id}>
                {project.title}
              </Text>
            ))}
          </View> */}
    </>
  );
}
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    // justifyContent: "center",
    // alignItems: "center",
  },
  project: {
    color: "#fff",
    fontSize: 120,
  },
});
```

Ok, uma das propriedades obrigatóіrias que o `**FlatList**` recebe é o `**data**`, que nada mais é nosso `objeto` de iteração, depois vem o `**keyExtractor**`, nele nos passamos nosso item `project` e tiramos dele uma propriedade única, que neste caso é o `id`, depois vem a propriedade `**renderItem**` que recebe uma função, essa função tem vários parâmetros, um deles é o item, que por si só é um Г­ndice do nosso objeto de iteração, via desetruturação nos conseguimos renomear esse parâmetro, assim fica mais fácil para nos familiarizar, e por fim o o componente a ser renderizado como retorno dessa função, que neste caso é o `<Text/>`, obtemos este resultado visual:

  <img src="https://i.imgur.com/HziqRB1.gif" width="200" height="400"/>

não existe diferença visual da `**ScrollView**` para a `**FlatList**`, porém se tivermos que renderizar uma lista muito grande, a `**FlatList**` vai ter muito mais performance que a `**ScrollView`, porque a `FlatList`** não renderiza itens que não estão visíveis, a `**FlatList**`também tem a funcionalidade de`**Refresh**`, agora vamos deixar esse Layout um pouco mais bonito utilizando o componente`**SafeAreaView\*\*`, segue o exemplo de aplicaГ§ГЈo abaixo:

```jsx
import React, { useEffect, useState } from "react";
import {
  View,
  Text,
  StyleSheet,
  StatusBar,
  FlatList,
  SafeAreaView,
} from "react-native";
import api from "./services/api";

export default function App() {
  const [projects, setProjects] = useState([]);

  useEffect(() => {
    api.get("/projects").then((response) => setProjects(response.data));
  }, []);

  return (
    <>
      <StatusBar barStyle="light-content" backgroundColor="#7159c1" />
      <SafeAreaView style={styles.container}>
        <FlatList
          data={projects}
          keyExtractor={(project) => project.id}
          renderItem={({ item: project }) => (
            <Text style={styles.project}>{project.title}</Text>
          )}
        />
      </SafeAreaView>
    </>
  );
}
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  project: {
    color: "#fff",
    fontSize: 20,
  },
});
```

Aqui está a visualização destas modificações:

  <img src="https://i.imgur.com/ktrwNlg.jpg" width="200" height="400"/>

Por fim Finalizamos essa parte :)

---

# Criando novos projetos

Aqui vamos seguir o mesmo exemplo da versГЈo [web](https://www.notion.so/Dia-04-Front-End-com-Reactjs-Guia-B-sico-de-Reactjs-b47b3be98b2246d08db740f72b5503f2)

Bem, agora vamos criar um botГЈo, para comeГ§ar a adicionar os projetos a nossa lista, e cadastrar na nossa `**api**`, abaixo o código dessa implementaГ§ГЈo:

```jsx
import React, { useEffect, useState } from "react";
import {
  Text,
  StyleSheet,
  StatusBar,
  FlatList,
  SafeAreaView,
  TouchableOpacity,
} from "react-native";
import api from "./services/api";

export default function App() {
  const [projects, setProjects] = useState([]);

  useEffect(() => {
    api.get("/projects").then((response) => setProjects(response.data));
  }, []);

  return (
    <>
      <StatusBar barStyle="light-content" backgroundColor="#7159c1" />
      <SafeAreaView style={styles.container}>
        <FlatList
          data={projects}
          keyExtractor={(project) => project.id}
          renderItem={({ item: project }) => (
            <Text style={styles.project}>{project.title}</Text>
          )}
        />
        <TouchableOpacity activeOpacity={0.6} style={styles.button}>
          <Text style={styles.buttonText}>Adicionar Projeto</Text>
        </TouchableOpacity>
      </SafeAreaView>
    </>
  );
}
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  project: {
    color: "#fff",
    fontSize: 20,
  },
  button: {
    backgroundColor: "#fff",
    alignSelf: "stretch",
    margin: 20,
    height: 50,
    borderRadius: 4,
    justifyContent: "center",
    alignItems: "center",
  },
  buttonText: {
    fontWeight: "bold",
    fontSize: 16,
  },
});
```

Com esse código obtemos o seguinte Feedback visual:

  <img src="https://i.imgur.com/wcCQUqf.jpg" width="200" height="400"/>

Agora vamos implementar a funcionalidade de adicionar novos `**projects**` a nossa lista.

```jsx
import React, { useEffect, useState } from "react";
import {
  Text,
  StyleSheet,
  StatusBar,
  FlatList,
  SafeAreaView,
  TouchableOpacity,
} from "react-native";
import api from "./services/api";

export default function App() {
  const [projects, setProjects] = useState([]);

  useEffect(() => {
    api.get("/projects").then((response) => setProjects(response.data));
  }, []);

  async function handleAddProject() {
    const response = await api.post("/projects", {
      owner: "Carlos Daniel",
      title: `Novo Projeto ${Date.now()}`,
    });
    const project = response.data;
    setProjects([...projects, project]);
  }

  return (
    <>
      <StatusBar barStyle="light-content" backgroundColor="#7159c1" />
      <SafeAreaView style={styles.container}>
        <FlatList
          data={projects}
          keyExtractor={(project) => project.id}
          renderItem={({ item: project }) => (
            <Text style={styles.project}>{project.title}</Text>
          )}
        />
        <TouchableOpacity
          activeOpacity={0.6}
          style={styles.button}
          onPress={handleAddProject}
        >
          <Text style={styles.buttonText}>Adicionar Projeto</Text>
        </TouchableOpacity>
      </SafeAreaView>
    </>
  );
}
const styles = StyleSheet.create({
  container: {
    backgroundColor: "#7159c1",
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  project: {
    color: "#fff",
    fontSize: 20,
  },
  button: {
    backgroundColor: "#fff",
    alignSelf: "stretch",
    margin: 20,
    height: 50,
    borderRadius: 4,
    justifyContent: "center",
    alignItems: "center",
  },
  buttonText: {
    fontWeight: "bold",
    fontSize: 16,
  },
});
```

Assim como fizemos na web, criamos uma função pra chamar a `api` adicionar um novo project la no nosso back-end, e jГЎ adicionamos o project ao fim da nossa lista.

---

 <img src="https://i.imgur.com/JpNFEBK.gif" width="200" height="400"/>

E fim :)

---
