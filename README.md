# 🚀 React Native + Expo + TypeScript Roadmap

Guia completo do **básico ao avançado**, com foco em prática, arquitetura e construção de um app real.

---

# 📦 Criação do Projeto (Template TypeScript)

## Criar projeto
```bash
npx create-expo-app app-react-native --template blank-typescript
cd app-react-native
npm install
```

## Executar projeto
```bash
npx expo start
```

## Executar no navegador
```bash
npx expo start --web
```

---

# 🧠 Base TypeScript

## 📚 Conteúdos
- function
- arrow function
- interface
- type
- enum

## 💻 Exemplo (App)
```tsx
import { View, Text } from 'react-native';

function saudacao(nome: string): string {
  return `Olá, ${nome}`;
}

const soma = (a: number, b: number): number => a + b;

type Status = 'loading' | 'success' | 'error';

enum Role {
  ADMIN = 'ADMIN',
  USER = 'USER',
}

interface User {
  name: string;
  role: Role;
}

export default function App() {
  const user: User = { name: 'Anderson', role: Role.ADMIN };

  return (
    <View style={{ padding: 20 }}>
      <Text>{saudacao(user.name)}</Text>
      <Text>Total: {soma(2, 3)}</Text>
      <Text>Role: {user.role}</Text>
    </View>
  );
}
```

---

# 🧠 Lógica de Programação

## 📚 Conteúdos
- if / else
- ternário
- map
- filter

## 💻 Exemplo (App)
```tsx
import { View, Text } from 'react-native';

export default function App() {
  const numbers = [10, 20, 30];
  const result = numbers.filter(n => n > 15);

  return (
    <View style={{ padding: 20 }}>
      {result.map((n, i) => (
        <Text key={i}>{n}</Text>
      ))}
    </View>
  );
}
```

---

# 📱 Fundamentos React Native

## 📚 Conteúdos
- View
- Text
- TextInput
- Button
- useState

## 💻 Exemplo (App)
```tsx
import { View, Text, TextInput, Button } from 'react-native';
import { useState } from 'react';

export default function App() {
  const [name, setName] = useState('');

  return (
    <View style={{ padding: 20 }}>
      <TextInput value={name} onChangeText={setName} />
      <Button title="Mostrar" onPress={() => alert(name)} />
    </View>
  );
}
```

---

# 🎨 Layout

## 📦 Instalação
```bash
npx expo install react-native-safe-area-context
```

## 💻 Exemplo (App)
```tsx
import { View, Text, StyleSheet } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Layout</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1, justifyContent: 'center', alignItems: 'center' }
});
```

---

# 🧭 Navegação

## 📦 Instalação
```bash
npm install @react-navigation/native
npm install @react-navigation/native-stack
npx expo install react-native-screens react-native-safe-area-context
```

## 💻 Exemplo (App)
```tsx
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import { View, Button, Text } from 'react-native';

const Stack = createNativeStackNavigator();

function Home({ navigation }: any) {
  return (
    <View>
      <Button title="Ir" onPress={() => navigation.navigate('Details')} />
    </View>
  );
}

function Details() {
  return <Text>Detalhes</Text>;
}

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={Home} />
        <Stack.Screen name="Details" component={Details} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

---

# 🌐 API

## 💻 Exemplo (App)
```tsx
import { useEffect, useState } from 'react';
import { FlatList, Text } from 'react-native';

export default function App() {
  const [data, setData] = useState<any[]>([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(res => res.json())
      .then(setData);
  }, []);

  return (
    <FlatList
      data={data}
      keyExtractor={(item) => item.id.toString()}
      renderItem={({ item }) => <Text>{item.name}</Text>}
    />
  );
}
```

---

# 💾 Persistência

## 📦 Instalação
```bash
npx expo install @react-native-async-storage/async-storage
```

## 💻 Exemplo (App)
```tsx
import AsyncStorage from '@react-native-async-storage/async-storage';
import { View, Button } from 'react-native';

export default function App() {
  const save = async () => {
    await AsyncStorage.setItem('token', '123');
  };

  return (
    <View>
      <Button title="Salvar" onPress={save} />
    </View>
  );
}
```

---

# 🌍 Context API

## 💻 Exemplo (App)
```tsx
import { createContext, useContext, useState } from 'react';
import { View, Text } from 'react-native';

const Context = createContext<any>(null);

function Child() {
  const { user } = useContext(Context);
  return <Text>{user}</Text>;
}

export default function App() {
  const [user] = useState('Anderson');

  return (
    <Context.Provider value={{ user }}>
      <View>
        <Child />
      </View>
    </Context.Provider>
  );
}
```

---

# 📸 Recursos Nativos

## 📦 Instalação
```bash
npx expo install expo-camera
```

## 💻 Exemplo (App)
```tsx
import { CameraView, useCameraPermissions } from 'expo-camera';
import { View, Button } from 'react-native';

export default function App() {
  const [permission, requestPermission] = useCameraPermissions();

  if (!permission?.granted) {
    return <Button title="Permitir" onPress={requestPermission} />;
  }

  return <CameraView style={{ flex: 1 }} />;
}
```

---

# 💣 Projeto Final

## Funcionalidades
- Login
- Lista
- API
- Navegação
- Context
- Persistência

---

🔥 Ready para produção!