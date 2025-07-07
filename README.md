[![Screenshot-1.png](https://i.postimg.cc/RVmXrW5L/Screenshot-1.png)](https://postimg.cc/8syhMPC7)

# HZ FiveM Artifacts DB

**Creado por HZ - Hazteunsitio.net**

Un sitio web simple que mantiene un **registro de artifacts de FiveM con problemas conocidos** y proporciona un enlace de descarga a los artifacts más recientes si no se han reportado problemas con ellos.

## 🚀 Características

- ✅ **Verificación automática de artifacts**: Identifica automáticamente el artifact más reciente sin problemas reportados
- 🔍 **Búsqueda de artifacts**: Busca artifacts específicos para verificar su estado
- 📱 **Interfaz responsive**: Diseño moderno y adaptable a todos los dispositivos
- 🌐 **API REST**: Endpoints para integración con otras aplicaciones
- ⚡ **Rendimiento optimizado**: Construido con Next.js 15 y React 19
- 🎨 **UI moderna**: Interfaz elegante con Tailwind CSS

## 🛠️ Tecnologías Utilizadas

- **Frontend**: Next.js 15, React 19, TypeScript
- **Estilos**: Tailwind CSS
- **Base de datos**: JSON estático (db.json)
- **Deployment**: Compatible con Vercel, Netlify, y otros

## 📋 Funcionalidades del Script

### 🔍 Verificación de Artifacts
El sistema verifica automáticamente los artifacts de FiveM contra una base de datos de problemas conocidos y recomienda el artifact más reciente que no tenga problemas reportados.

### 📊 Base de Datos de Problemas
Mantiene un registro actualizado de artifacts con problemas conocidos, incluyendo:
- Crashes del servidor
- Problemas de conectividad
- Errores de compilación
- Incompatibilidades
- Problemas de rendimiento

### 🔗 Enlaces de Descarga
Genera automáticamente enlaces de descarga para:
- **Windows**: Servidor de FiveM para Windows
- **Linux**: Servidor de FiveM para Linux

### 🌐 API REST
Proporciona endpoints para integración:
- `/check?artifact=XXXX`: Verifica un artifact específico
- `/json`: Datos completos en formato JSON

## 🚀 Instalación y Uso

### Prerrequisitos
- Node.js 18 o superior
- npm o yarn

### Instalación

1. **Clona el repositorio**:
   ```bash
   git clone <tu-repositorio>
   cd hz-fivem-artifacts-db
   ```

2. **Instala las dependencias**:
   ```bash
   npm install
   # o
   yarn install
   ```

3. **Ejecuta en modo desarrollo**:
   ```bash
   npm run dev
   # o
   yarn dev
   ```

4. **Abre tu navegador** en `http://localhost:3000`

### Construcción para Producción

```bash
npm run build
npm start
```

## 📡 API Documentation

### Verificar Artifact Específico

**Endpoint**: `/check?artifact=XXXX`

**Método**: GET

**Parámetros**:
- `artifact` (string): Número del artifact a verificar

**Respuesta**:
```json
{
  "status": "OK" | "BROKEN",
  "reason": "string" // Solo si status es "BROKEN"
}
```

**Ejemplo**:
```bash
curl "https://tu-dominio.com/check?artifact=12345"
```

### Obtener Datos Completos

**Endpoint**: `/json`

**Método**: GET

**Respuesta**:
```json
{
  "recommendedArtifact": "string",
  "windowsDownloadLink": "string",
  "linuxDownloadLink": "string",
  "brokenArtifacts": {
    "artifact_number": "reason"
  }
}
```

## 🔧 Configuración

### Actualizar Base de Datos de Artifacts

Edita el archivo `db.json` para agregar o modificar artifacts con problemas:

```json
{
  "brokenArtifacts": {
    "12345": "Descripción del problema",
    "12346-12350": "Problema que afecta un rango de artifacts"
  }
}
```

### Personalización

- **Colores y estilos**: Modifica `tailwind.config.ts`
- **Metadatos**: Actualiza `app/layout.tsx`
- **Contenido**: Edita los componentes en `app/`

## 🤝 Contribuir

### Reportar Problemas de Artifacts

1. **Crea un issue** con evidencia del problema
2. **Incluye**:
   - Número del artifact
   - Descripción detallada del problema
   - Logs de error (si aplica)
   - Enlaces a issues de GitHub de Cfx

### Contribuir al Código

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -am 'Agrega nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Crea un Pull Request

## 📁 Estructura del Proyecto

```
hz-fivem-artifacts-db/
├── actions/
│   └── fivem.ts          # Lógica de negocio para artifacts
├── app/
│   ├── check/
│   │   └── route.ts      # API endpoint para verificar artifacts
│   ├── json/
│   │   └── route.ts      # API endpoint para datos completos
│   ├── brokenArtifacts.tsx # Componente de artifacts rotos
│   ├── globals.css       # Estilos globales
│   ├── layout.tsx        # Layout principal
│   └── page.tsx          # Página principal
├── db.json               # Base de datos de artifacts rotos
├── package.json          # Dependencias y scripts
├── tailwind.config.ts    # Configuración de Tailwind
├── tsconfig.json         # Configuración de TypeScript
└── README.md             # Este archivo
```

## 🔒 Seguridad

- No se almacenan datos sensibles
- Todas las consultas son de solo lectura
- Rate limiting recomendado para producción
- HTTPS recomendado para deployment

## 📈 Rendimiento

- **SSG**: Generación estática para páginas principales
- **ISR**: Revalidación incremental para datos de artifacts
- **Caching**: Cache de 24 horas para datos de GitHub
- **Optimización**: Imágenes y assets optimizados

## 🌐 Deployment

### Vercel (Recomendado)

1. Conecta tu repositorio a Vercel
2. Configura las variables de entorno (si las hay)
3. Deploy automático en cada push

### Netlify

1. Conecta tu repositorio a Netlify
2. Build command: `npm run build`
3. Publish directory: `.next`

### Docker

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

## 📊 Monitoreo

- Logs de acceso a API
- Métricas de rendimiento
- Alertas de artifacts rotos
- Uptime monitoring

## 🆘 Soporte

- **Website**: [Hazteunsitio.net](https://hazteunsitio.net)
- **Email**: contacto@hazteunsitio.net
- **Issues**: Crea un issue en este repositorio

## 📄 Licencia

Este proyecto está liberado al dominio público. Puedes leer la licencia completa en [LICENSE](./LICENSE).

## ⚖️ Legal

"FiveM" es una marca registrada de Take-Two Interactive Software, Inc.

---

**© 2025 HZ - Hazteunsitio.net | Todos los derechos reservados**

*Creado con ❤️ por HZ - Hazteunsitio.net*
