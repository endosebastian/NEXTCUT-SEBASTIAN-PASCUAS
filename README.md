# ✂️ NEXTCUT — Sistema de Reservas para Peluquería

Sistema web profesional de gestión de citas para peluquería/barbería, construido en HTML puro con Firebase Firestore como base de datos en tiempo real. No requiere servidor ni instalación.

---

## 🚀 Tecnologías utilizadas

- **HTML5 / CSS3 / JavaScript** — sin frameworks, corre directo en el navegador
- **Firebase Firestore** — base de datos en la nube para usuarios, servicios y reservas
- **Google Fonts** — tipografías Playfair Display y DM Sans
- **Unsplash** — imágenes de fondo dinámicas de peluquería

---

## 📁 Estructura del proyecto

```
peluqueria_v3.html   ← archivo único, todo incluido
README.md
```

El sistema completo vive en un solo archivo HTML. No hay dependencias locales que instalar.

---

## ✨ Funcionalidades

### 👤 Clientes
- Registro con usuario y contraseña
- Inicio de sesión
- Ver catálogo de servicios con precios
- Reservar cita por fecha y hora (horarios de 9am a 5pm, lunes a viernes, sin hora de almuerzo)
- Ver y cancelar sus propias reservas
- **Vincular número de celular** desde "Mi perfil" para que el barbero pueda contactarlos
- Ver el contacto directo del barbero con botón de llamada

### 👑 Administrador
- Acceso con credenciales especiales (`Admn1234` / `Admn1234`)
- Añadir servicios con nombre y precio
- Ver y eliminar servicios registrados
- Editar nombre y precio de cualquier servicio
- Ver todas las reservas agrupadas por cliente
- Ver el número de teléfono vinculado de cada cliente con enlace de llamada directa
- **Cancelar cualquier cita** desde el panel

### 📱 Teléfono vinculado
Cada cliente puede ir a **Mi perfil** e ingresar su número con prefijo internacional (por defecto `+57`). Este número queda guardado en Firebase y visible para el administrador, con un botón que abre el marcador del teléfono directamente.

---

## 🔐 Credenciales de administrador

| Campo    | Valor      |
|----------|------------|
| Usuario  | `Admn1234` |
| Contraseña | `Admn1234` |

> ⚠️ Se recomienda cambiar estas credenciales en producción directamente en el código fuente.

---

## 📞 Contacto del barbero

El número **314 688 3890** aparece en el menú principal del cliente con un botón de llamada directa. Para cambiarlo, busca en el HTML:

```html
<a href="tel:+573146883890" ...>📱 Llamar</a>
```

y reemplaza el número en el `href` y en el texto visible.

---

## 🗄️ Colecciones en Firebase Firestore

| Colección  | Campos                                      |
|------------|---------------------------------------------|
| `usuarios` | `user`, `pass`, `phone`                     |
| `servicios`| `name`, `price`                             |
| `reservas` | `user`, `phone`, `service`, `price`, `date`, `time` |

---

## 🕐 Horarios disponibles para reservas

El sistema genera slots automáticamente en este rango:

- **Mañana:** 9:00 – 11:30 (cada 30 min)
- **Tarde:** 13:00 – 16:30 (cada 30 min)
- **Hora de almuerzo (12:00):** bloqueada automáticamente
- Los slots ya reservados no aparecen disponibles

---

## 🖼️ Fondos dinámicos

El fondo cambia según la sección activa (login, registro, catálogo, reservas, admin, etc.) con una transición suave. Todas las imágenes se cargan desde Unsplash con IDs fijos para evitar errores.

---

## ▶️ Cómo usar

1. Abrir `peluqueria_v3.html` en cualquier navegador moderno (Chrome, Firefox, Edge, Safari)
2. Crear una cuenta como cliente o ingresar como administrador
3. El cliente puede reservar citas, ver sus reservas y vincular su teléfono
4. El administrador gestiona servicios y ve todas las citas con datos de contacto

> No se necesita conexión a servidor propio. Firebase maneja todo en la nube automáticamente.

---

## 🛠️ Personalización rápida

| Qué cambiar | Dónde buscarlo en el HTML |
|---|---|
| Nombre del negocio | `✂ NEXTCUT` en el `<div class="brand">` |
| Número del barbero | `tel:+573146883890` y el texto `314 688 3890` |
| Credenciales admin | `const ADMIN_USER` y `const ADMIN_PASS` |
| Colores principales | Variables CSS `:root` (`--gold`, `--dark`, etc.) |
| Horario de atención | Función `mostrarHorarios()` en el script |

---

## 📄 Licencia

Proyecto de uso privado para la peluquería. No distribuir sin autorización.
