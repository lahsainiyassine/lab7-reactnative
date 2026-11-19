# Lab 7 : Créer un champ de saisie et un écran de connexion avec TextInput

- **URL de la plateforme** : https://mliaedu.toubkalit.com/student/courses/38/labs/244
- **Formation** : React Native

---

## 1. Objectifs
À la fin de ce TP, l’étudiant :
- Configure un composant `TextInput` pour saisir du texte ;
- Stocke ce texte dans l’état local avec `useState` ;
- Utilise des props de `TextInput` :
  - `placeholder`
  - `keyboardType`
  - `secureTextEntry`
- Applique un style simple pour obtenir une interface propre.

Le TP se déroule en **deux parties** :
1. Un écran d’accueil avec un champ “First Name”.
2. Un écran de connexion avec email et mot de passe.

---

## 2. Pré-requis
- Projet React Native déjà créé (Expo ou React Native CLI).
- Notions de base :
  - Composants fonctionnels
  - Hooks React (`useState`)
  - `StyleSheet` et styles basiques.
- Composants `AppHeader` et `AppFooter`.

---

## 3. Étape 1 : WelcomeScreen avec TextInput
**Fichier : `components/WelcomeScreen.js`**
```javascript
import React, { useState } from 'react';
import { ScrollView, Text, StyleSheet, TextInput } from 'react-native';

export default function WelcomeScreen() {
  const [firstName, onChangeFirstName] = useState('');

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.headerText}>Welcome to My App</Text>
      <Text style={styles.regularText}>
        This is a simple demo application. Please enter your name below.
      </Text>

      <TextInput
        style={styles.inputBox}
        value={firstName}
        onChangeText={onChangeFirstName}
        placeholder="First Name"
      />
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#333333',
  },
  headerText: {
    padding: 40,
    fontSize: 30,
    color: '#EDEFEE',
    textAlign: 'center',
  },
  regularText: {
    fontSize: 24,
    padding: 20,
    marginVertical: 8,
    color: '#EDEFEE',
    textAlign: 'center',
  },
  inputBox: {
    height: 40,
    marginHorizontal: 20,
    marginVertical: 12,
    paddingHorizontal: 10,
    borderWidth: 1,
    borderColor: '#EDEFEE',
    borderRadius: 8,
    fontSize: 18,
    backgroundColor: '#FFFFFF',
    color: '#000000',
  },
});
```

---

## 4. Étape 2 : LoginScreen avec Email et Password
**Fichier : `components/LoginScreen.js`**
```javascript
import React, { useState } from 'react';
import { ScrollView, Text, StyleSheet, TextInput } from 'react-native';

export default function LoginScreen() {
  const [email, onChangeEmail] = useState('');
  const [password, onChangePassword] = useState('');

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.headerText}>Welcome</Text>
      <Text style={styles.regularText}>Login to continue</Text>

      <TextInput
        style={styles.inputBox}
        value={email}
        onChangeText={onChangeEmail}
        placeholder="Email"
        keyboardType="email-address"
      />

      <TextInput
        style={styles.inputBox}
        value={password}
        onChangeText={onChangePassword}
        placeholder="Password"
        keyboardType="default"
        secureTextEntry={true}
      />
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#333333',
  },
  headerText: {
    padding: 40,
    fontSize: 30,
    color: '#EDEFEE',
    textAlign: 'center',
  },
  regularText: {
    fontSize: 24,
    padding: 20,
    marginVertical: 8,
    color: '#EDEFEE',
    textAlign: 'center',
  },
  inputBox: {
    height: 40,
    marginHorizontal: 20,
    marginVertical: 12,
    paddingHorizontal: 10,
    borderWidth: 1,
    borderColor: '#EDEFEE',
    borderRadius: 8,
    fontSize: 18,
    backgroundColor: '#FFFFFF',
    color: '#000000',
  },
});
```

---

## 5. Étape 3 : Intégration dans App.js
**Fichier : `App.js`**
```javascript
import * as React from 'react';
import { View, StyleSheet } from 'react-native';

import AppHeader from './components/AppHeader';
import AppFooter from './components/AppFooter';
import LoginScreen from './components/LoginScreen';

export default function App() {
  return (
    <>
      <View style={styles.container}>
        <AppHeader />
        <LoginScreen />
      </View>
      <View style={styles.footerContainer}>
        <AppFooter />
      </View>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#333333',
  },
  footerContainer: {
    backgroundColor: '#333333',
  },
});
```
