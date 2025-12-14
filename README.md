# ump-index

Registry oficial para paquetes y librerías de UMP (Umbral Package Manager).

## Descripción

Este repositorio contiene el archivo `global_directory.yml`, que funciona como un indice oficial para las librerías disponibles en el ecosistema de Umbral. Los usuarios pueden instalar estas librerías en sus proyectos usando el comando:

```bash
ump add <nombre-libreria>
```

## Estructura del Registry

Cada entrada en `global_directory.yml` sigue esta estructura:

```yaml
nombre-libreria:
  repository: usuario/nombre-repo
  umbral: ">=version-minima"
  exports:
    - funcion1
    - funcion2
```

### Campos

- **nombre-libreria**: Nombre de la librería (clave principal, en minúsculas)
- **repository**: Nombre del repositorio en formato `usuario/nombre-repo` (sin URL completa)
- **umbral**: Versión mínima de Umbral requerida (formato semver con operador)
- **exports** (opcional): Lista de funciones o clases exportadas por la librería

### Ejemplo

```yaml
http:
  repository: hersac/umbral-http
  umbral: ">=0.1.0"
  exports:
    - fetch
    - HttpClient
```

## Cómo Registrar tu Librería

Sigue estos pasos para agregar tu librería al registry:

### 1. Fork del Repositorio

Haz un fork de este repositorio a tu cuenta de GitHub.

### 2. Edita el Archivo `global_directory.yml`

Clona tu fork y edita el archivo `global_directory.yml`:

```bash
git clone https://github.com/hersac/ump-index.git
cd ump-index
```

### 3. Agrega tu Librería

Agrega tu entrada **en orden alfabético** siguiendo la estructura requerida:

```yaml
mi-libreria:
  repository: mi-usuario/mi-repo-umbral
  umbral: ">=0.1.0"
  exports:
    - miFuncion
    - MiClase
```

**Reglas obligatorias:**

- ✅ Orden alfabético por nombre de librería
- ✅ Solo el nombre del repositorio (formato `usuario/repo`), sin URL completa
- ✅ Versión mínima de Umbral requerida
- ✅ Campo `exports` es opcional (omitir si no aplica)
- ✅ Usar comillas dobles para versiones
- ✅ Mantener la indentación de 2 espacios

### 4. Commit y Push

```bash
git add global_directory.yml
git commit -m "Agregar librería: mi-libreria"
git push origin main
```

### 5. Crear Pull Request

Crea un Pull Request desde tu fork hacia el repositorio principal. Asegúrate de:

- Describir brevemente tu librería
- Confirmar que cumple con la estructura requerida
- Verificar que está en orden alfabético

## Validación

Antes de enviar tu PR, verifica que:

- [ ] El nombre de la librería debe coincidir con el campo `name` definido en su `umpkg.yml` de la librería que estás agregando
- [ ] La entrada está en orden alfabético
- [ ] El formato YAML es válido
- [ ] El campo `repository` solo contiene `usuario/repo`
- [ ] La versión de Umbral usa el formato correcto
- [ ] Los `exports` están listados correctamente (si aplica)

## Licencia

Este proyecto está bajo la licencia especificada en el archivo [LICENSE](LICENSE).
