# Seguimiento Epilepsia — Guía de publicación en Play Store

---

## ARCHIVOS DEL PROYECTO

```
facu-epilepsia-app/
├── index.html               ← La app completa (v1.1)
├── manifest.json            ← Configuración PWA
├── sw.js                    ← Service Worker (funciona sin internet)
├── icons/
│   ├── icon-192.png         ← DEBES CREAR este ícono (192×192 px)
│   └── icon-512.png         ← DEBES CREAR este ícono (512×512 px)
├── GUIA-PLAY-STORE.md       ← Este archivo
└── POLITICA-PRIVACIDAD.txt  ← Texto para Google Sites
```

---

## NOVEDADES v1.1

- Carga de ataques anteriores (fecha + hora en hora en hora)
- Medicamentos: 3 fijos + 3 campos personalizables con nombre libre
- Importación de historial desde Excel (.xlsx) o CSV
- Botón exportar visible en Historial y en Perfil

---

## PASO 1 — CREAR LOS ÍCONOS

Dos imágenes PNG cuadradas del ícono de tu app.

**En Canva (gratis):**
1. Ir a https://www.canva.com
2. Crear diseño 512×512 px
3. Diseñar ícono (cerebro, corazón, cruz médica, etc.)
4. Descargar PNG → guardar como `icons/icon-512.png`
5. Redimensionar a 192×192 → guardar como `icons/icon-192.png`

Requisitos: fondo sólido (no transparente), formato PNG.

---

## PASO 2 — SUBIR A GITHUB

1. Crear cuenta en https://github.com
2. Crear repositorio: nombre `epilepsia-app`, visibilidad **Público**
3. Subir TODOS los archivos (incluyendo carpeta `icons/`)

---

## PASO 3 — PUBLICAR CON VERCEL

1. Ir a https://vercel.com → registrarse con GitHub
2. "Add New Project" → seleccionar `epilepsia-app`
3. Clic en **Deploy**

URL resultado: `https://epilepsia-app.vercel.app`

Desde el celular Android: abrir la URL → aparece opción
"Agregar a pantalla de inicio" → ya funciona como app instalada.

---

## PASO 4 — INSTALAR NODE.JS

Descargar versión LTS desde: https://nodejs.org

Verificar en terminal:
```
node --version
npm --version
```

---

## PASO 5 — GENERAR EL APK CON BUBBLEWRAP

```bash
# Instalar Bubblewrap
npm install -g @bubblewrap/cli

# Inicializar (reemplazá la URL por la tuya)
bubblewrap init --manifest https://epilepsia-app.vercel.app/manifest.json

# Durante la configuración:
# Application ID: com.tuapellido.epilepsia
# Display name: Seguimiento Epilepsia
# (resto en valores por defecto → Enter)

# Construir
bubblewrap build
```

Archivos generados:
- `app-release-bundle.aab` → subir a Play Store
- `app-release-signed.apk` → instalar en tu celular para probar

---

## PASO 6 — PUBLICAR EN GOOGLE PLAY

### Crear la aplicación
1. https://play.google.com/console
2. "Crear aplicación"
3. Nombre: `Seguimiento Epilepsia`
4. Tipo: Aplicación · Gratuita
5. Aceptar políticas → Crear

### Ficha de Play Store
Menú → Presencia en Play Store → Ficha principal

**Descripción breve (80 caracteres):**
```
Registrá crisis epilépticas, medicación y compartí con el médico.
```

**Descripción completa:**
```
App para el seguimiento diario de crisis epilépticas en niños.

FUNCIONES:
• Botón de registro rápido con confirmación de hora
• Carga de ataques anteriores (fecha y hora)
• Medicamentos configurables: hasta 6 medicamentos (3 fijos + 3 a tu nombre)
• Historial con estadísticas: total, promedio, mejor y peor día
• Gráfico de crisis diarias con líneas de medicación día a día
• Distribución de ataques por hora del día
• Importación de historial desde Excel o CSV
• Exportación a CSV para enviar al médico por correo o WhatsApp

DISEÑADA PARA FAMILIAS:
• Perfil personalizable con nombre y edad del paciente
• 5 colores de interfaz a elegir
• Funciona sin internet
• Interfaz simple y clara, sin tecnicismos

Los datos se guardan localmente en el dispositivo.
```

**Recursos gráficos necesarios:**
- Ícono: 512×512 PNG
- Capturas de pantalla: mínimo 2 fotos de la app en el celular
- Imagen de portada: 1024×500 PNG (hacerla en Canva)

**Categoría:** Salud y bienestar

### Política de privacidad (obligatoria)
Ver archivo `POLITICA-PRIVACIDAD.txt` para el texto.
Publicarlo en https://sites.google.com y copiar la URL en Play Console.

### Subir el AAB
1. Menú → Producción → Crear nueva versión
2. Subir `app-release-bundle.aab`
3. Notas: `Versión inicial 1.0`
4. Guardar → Revisar → Lanzar en producción

⏳ Revisión de Google: 1 a 3 días hábiles.

---

## FLUJO COMPLETO

```
Íconos PNG  →  GitHub  →  Vercel (URL pública)
                                   ↓
                           Bubblewrap (AAB)
                                   ↓
                           Play Console
                                   ↓
                        Revisión Google (1-3 días)
                                   ↓
                          ✅ App en Play Store
```

---

## ACTUALIZACIONES FUTURAS

1. Modificar `index.html`
2. Subir cambios a GitHub (Vercel se actualiza automático)
3. Ejecutar `bubblewrap build` nuevamente
4. Subir nuevo `.aab` en Play Console como nueva versión
