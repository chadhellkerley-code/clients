# Despliegue

Necesitás tener Node.js instalado. Después, desde una terminal:

```bash
npm install -g firebase-tools
firebase login
```

Se va a abrir el navegador para que inicies sesión con la cuenta de Google
que usaste para crear el proyecto "clientes-content".

Después, parado en esta carpeta (la que contiene `firebase.json`):

```bash
firebase deploy --only hosting,firestore:rules
```

Eso sube el sitio a `https://clientes-content.web.app` y aplica las reglas
de seguridad de Firestore.

- La página de clientes queda en la raíz: `https://clientes-content.web.app`
- El panel de administrador queda en: `https://clientes-content.web.app/admin`

## Importante: dominio autorizado

Firebase Hosting ya agrega automáticamente `clientes-content.web.app` y
`clientes-content.firebaseapp.com` a la lista de dominios autorizados para el
login por email, así que no hace falta tocar nada ahí salvo que más adelante
conectes un dominio propio (en ese caso: Authentication → Configuración →
Dominios autorizados → agregar el dominio nuevo).

## Cada vez que Claude te pase una versión nueva

Solo hace falta volver a correr:

```bash
firebase deploy --only hosting
```

(agregá `,firestore:rules` al final si también cambiaron las reglas).
