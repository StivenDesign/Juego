# SIN FILTRO 🔥 – Preguntas Incómodas

Juego web real para **exactamente dos personas**, con Express + Socket.IO, 200 preguntas originales (25 por cada una de 8 categorías), cinco niveles, turnos, puntuación, saltos sin penalización y reconexión.

## Carpetas

```text
sin-filtro/
├── public/
│   ├── index.html
│   ├── style.css
│   └── app.js
├── server.js
├── questions.js
├── package.json
├── .env.example
├── .gitignore
├── render.yaml
├── test.js
└── README.md
```

## Ejecutar en tu computador

1. Instala Node.js 20 o superior.
2. Abre una terminal dentro de esta carpeta.
3. Ejecuta `npm install` y luego `npm start`.
4. Abre `http://localhost:3000` en el navegador. Para probar dos personas localmente, abre otra pestaña. Ejecuta `npm test` para verificar preguntas y servidor.

## Subir a GitHub

Crea un repositorio **vacío** en GitHub llamado `sin-filtro` (sin README adicional). Desde la carpeta del proyecto ejecuta:

```bash
git init
git add .
git commit -m "Juego multijugador SIN FILTRO"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/sin-filtro.git
git push -u origin main
```

Sustituye `TU_USUARIO` por tu usuario real. GitHub puede pedirte iniciar sesión.

## Publicar en Render (plan gratuito)

1. Entra a Render y crea una cuenta.
2. Selecciona **New > Blueprint** y conecta tu cuenta de GitHub.
3. Elige el repositorio `sin-filtro`; Render detectará `render.yaml`.
4. Confirma la creación del servicio gratuito. Si usas **New > Web Service** en su lugar, selecciona Node, build command `npm install`, start command `npm start` y plan Free.
5. Espera a que termine el despliegue. Abre la dirección pública `https://NOMBRE-QUE-TE-ASIGNE.onrender.com` (el nombre real aparece en tu panel).
6. En el primer teléfono entra, escribe tu nombre y pulsa **Crear sala privada**. Comparte el enlace con **Copiar invitación** o el código de seis caracteres.
7. La segunda persona abre la misma web en otro dispositivo, escribe su nombre y pulsa **Entrar a la sala** con el código. Ambos verán las mismas preguntas y los turnos en tiempo real.

## Reglas y límites

- La persona de turno responde oralmente, por chat externo o llamada y pulsa **Respuesta completada** para sumar un punto. No se almacenan respuestas personales. Pasar no resta puntos. Las 200 preguntas se agotan sin repetirse en cada ronda.
- El código privado sirve para invitar, no es una contraseña de alta seguridad: compártelo solo con quien jugará.
- La sesión se conserva en `sessionStorage` para reconectar al recargar la misma pestaña. No borres sus datos ni cierres la pestaña si deseas conservar el token. Si se corta Internet, Socket.IO reintenta automáticamente.
- Las salas viven **solo en la memoria del servidor**. Si Render duerme, reinicia o redespliega la instancia, las partidas activas desaparecen. El plan gratuito puede tardar en despertar. No se necesita base de datos, pero esta versión está diseñada para **una sola instancia de servidor**.
- El botón **Abandonar sala** la cierra para ambas personas. **Volver a jugar** aparece al agotar las preguntas; cualquiera de los dos puede iniciarlo.
- Las preguntas aumentan por nivel; el orden dentro de cada nivel es aleatorio. El juego requiere Internet para dos dispositivos separados.
