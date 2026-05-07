# Seguimiento Epilepsia — Guía de publicación en Play Store

---

## ARCHIVOS DEL PROYECTO

```
facu-epilepsia-app/
├── index.html          ← La app completa
├── manifest.json       ← Configuración PWA
├── sw.js               ← Service Worker (funciona sin internet)
├── icons/
│   ├── icon-192.png    ← Ícono 192×192 px  ← DEBES CREARLO
│   └── icon-512.png    ← Ícono 512×512 px  ← DEBES CREARLO
└── README.md
```

---

## PASO 1 — CREAR LOS ÍCONOS (obligatorio)

Necesitás dos imágenes PNG cuadradas del ícono de tu app.

**Opción fácil — Canva (gratuito):**
1. Ir a https://www.canva.com
2. Crear diseño personalizado: 512×512 px
3. Diseñar el ícono (por ejemplo: cerebro, corazón, cruz médica)
4. Descargar como PNG → guardarlo como `icons/icon-512.png`
5. Repetir redimensionando a 192×192 → `icons/icon-192.png`

**Requisito Play Store:**
- Fondo no transparente (color sólido)
- Sin texto demasiado pequeño
- Formato PNG

---

## PASO 2 — SUBIR A GITHUB

1. Crear cuenta en https://github.com (si no tenés)
2. Crear repositorio nuevo:
   - Nombre: `epilepsia-app`
   - Visibilidad: **Público**
3. Subir TODOS los archivos de esta carpeta al repositorio
   (incluyendo la carpeta `icons/` con los dos íconos)

---

## PASO 3 — PUBLICAR CON VERCEL (gratis, 5 minutos)

1. Ir a https://vercel.com
2. Registrarse con tu cuenta de GitHub
3. Clic en **"Add New Project"**
4. Seleccionar el repositorio `epilepsia-app`
5. Clic en **"Deploy"**

✅ Vercel te da una URL como: `https://epilepsia-app.vercel.app`

Con esa URL la app ya funciona en cualquier celular.
Desde el celular Android aparece la opción "Agregar a pantalla de inicio".

---

## PASO 4 — INSTALAR NODE.JS (necesario para Bubblewrap)

Descargar desde: https://nodejs.org
Instalar la versión **LTS** (la recomendada).

Verificar instalación abriendo la terminal (cmd en Windows):
```
node --version
npm --version
```

---

## PASO 5 — GENERAR EL APK CON BUBBLEWRAP

Bubblewrap es la herramienta oficial de Google para convertir PWAs en apps Android.

**En la terminal, ejecutar:**

```bash
# Instalar Bubblewrap
npm install -g @bubblewrap/cli

# Crear el proyecto Android (reemplazá la URL por la tuya de Vercel)
bubblewrap init --manifest https://epilepsia-app.vercel.app/manifest.json

# Durante la configuración te pedirá:
# - Application ID: com.tuapellido.epilepsia  (ej: com.garcia.epilepsia)
# - Display name: Seguimiento Epilepsia
# - Dejar el resto en valores por defecto (presionar Enter)

# Construir el APK/AAB
bubblewrap build
```

Esto genera dos archivos en la carpeta del proyecto:
- `app-release-bundle.aab` ← Este es el que subís a Play Store
- `app-release-signed.apk` ← Para pruebas en tu celular

**Para instalar en tu celular y probar antes de publicar:**
Pasá el `.apk` a tu celular por WhatsApp o cable y abrilo.
(Puede que pida activar "Instalar apps de fuentes desconocidas" en Ajustes)

---

## PASO 6 — PUBLICAR EN GOOGLE PLAY STORE

Ya tenés cuenta en Google Play Console. Estos son los pasos:

### 6a. Crear la aplicación
1. Ir a https://play.google.com/console
2. Clic en **"Crear aplicación"**
3. Idioma predeterminado: Español
4. Nombre: `Seguimiento Epilepsia`
5. Tipo: Aplicación
6. Gratuita o de pago: **Gratuita**
7. Aceptar las políticas y crear

### 6b. Completar la ficha de Play Store
En el menú izquierdo → **"Presencia en Play Store" → "Ficha de Play Store principal"**

Completar:
- **Descripción breve** (80 caracteres):
  `Registrá crisis epilépticas, medicación y compartí el historial con el médico.`

- **Descripción completa** (4000 caracteres máximo):
  ```
  App para el seguimiento diario de crisis epilépticas en niños.
  
  FUNCIONES PRINCIPALES:
  • Botón de registro rápido con confirmación de hora
  • Control de medicamentos diarios (Kepra, Depakene, Trileptal)
  • Historial con estadísticas: total, promedio, mejor y peor día
  • Gráfico de crisis diarias con líneas de medicación
  • Distribución de ataques por hora del día
  • Exportación a CSV para enviar al médico por correo o WhatsApp
  
  DISEÑADA PARA FAMILIAS:
  • Perfil personalizable con nombre y edad del paciente
  • Funciona sin internet
  • Interfaz simple y clara
  
  Los datos se guardan de forma local en el dispositivo.
  ```

- **Íconos y capturas de pantalla:**
  - Ícono de app: 512×512 PNG (el que creaste)
  - Capturas de pantalla: al menos 2 fotos de la app funcionando en el celular
  - Imagen de portada: 1024×500 PNG (podés hacerla en Canva)

### 6c. Configurar la app
En **"Configuración de la app"**:
- Categoría: **Salud y bienestar**
- Etiquetas: epilepsia, salud, médico, niños
- Política de privacidad: necesitás una URL (ver nota abajo)

### 6d. Política de privacidad (obligatoria)
Google requiere una URL con la política de privacidad.

**Opción fácil:** Crear una página en https://sites.google.com con este texto:

```
Política de Privacidad — Seguimiento Epilepsia

Esta aplicación almacena todos los datos exclusivamente en el 
dispositivo del usuario. No se recopila, transmite ni comparte 
ningún dato personal con terceros. Los datos solo existen en 
el celular donde se usa la app.

Para eliminar todos los datos, desinstalar la aplicación.

Contacto: [tu email]
```

### 6e. Subir el AAB y publicar
1. Menú izquierdo → **"Producción"** → **"Crear nueva versión"**
2. Subir el archivo `app-release-bundle.aab`
3. Notas de la versión: `Versión inicial`
4. Clic en **"Guardar"** y luego **"Revisar versión"**
5. Clic en **"Comenzar lanzamiento en producción"**

⏳ Google tarda entre 1 y 3 días en revisar y aprobar la app.
Una vez aprobada, aparece en Play Store y podés buscarla por nombre.

---

## ACTUALIZACIONES FUTURAS

Cuando quieras actualizar la app:
1. Modificar el `index.html`
2. Subir los cambios a GitHub (Vercel se actualiza automático)
3. En `manifest.json`, no es necesario cambiar nada
4. Para actualizar en Play Store: volver a ejecutar `bubblewrap build`
   y subir el nuevo `.aab` en Play Console como nueva versión

---

## RESUMEN DEL PROCESO

```
Íconos PNG  →  GitHub  →  Vercel (URL pública)
                                    ↓
                            Bubblewrap (genera .aab)
                                    ↓
                            Play Console (sube .aab)
                                    ↓
                         Revisión Google (1-3 días)
                                    ↓
                            ✅ App en Play Store
```

---

## AYUDA

Para cualquier duda en el proceso, continuá la conversación con Claude.
Podés preguntar sobre cada paso con el mensaje exacto del error que te aparezca.
