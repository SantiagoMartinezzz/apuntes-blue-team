# apuntes-blue-team
Notes and documentation on defensive cybersecurity (Blue Team) and automation with Bash and Python during my learning journey

# 🛡️ Mis Apuntes de Blue Team

## 🌐 Reconocimiento y Enumeración Web

### Herramienta: `dirb`
Se utiliza en la terminal para descubrir páginas y directorios ocultos en un sitio web mediante un diccionario de palabras comunes (como *login* o *admin*).

**Estructura del comando:**
```bash
dirb http://[IP_OBJETIVO]
```

**Ejemplo del laboratorio de TryHackMe:**
```bash
dirb http://10.10.134.195
```

## 🛡️ Análisis Defensivo (Caso FakeBank)

### El Ataque (Lo que descubrimos)
- Un atacante pudo usar `dirb` para listar directorios y encontrar el panel `/bank-transfer`.
- El panel no requería ningún tipo de inicio de sesión o autenticación, lo que permitió realizar una transferencia de \$2,000 USD sin autorización.

### La Solución del Blue Team (Remediación)
1. **Controles de Acceso Estrictos:** No basta con ocultar las páginas. Se debe **requerir login** obligatorio para acceder a cualquier panel administrativo.
2. **Principio de Menor Privilegio:** Limitar el acceso a ese panel únicamente a las direcciones IP internas de la empresa o a través de una VPN corporativa.
3. **Monitoreo de Logs:** Configurar un script de automatización o un sistema SIEM para detectar picos anormales de peticiones web (fuerza bruta de directorios) y bloquear automáticamente las IPs que intenten escanear el sitio.


   ## 🕵️‍♂️ Módulo: Introducción a la Seguridad Defensiva (SOC)

### Conceptos Clave
- **SOC (Security Operations Centre):** Centro donde se monitorea y defiende la infraestructura digital.
- **Fuerza Bruta:** Ataque automatizado con cientos de intentos de login para adivinar credenciales (ej. el ataque al usuario `dave.saunders`).
- **Threat Intelligence (Inteligencia de Amenazas):** Recolección y documentación de datos de ataques (IPs, usuarios, URLs, nombres de grupos de hackers) para compartirlos con la comunidad y prevenir futuros incidentes.

### Buenas Prácticas del Analista SOC
- Al mitigar una amenaza, siempre se debe registrar el incidente en bases de datos de inteligencia. Documentar el origen, el objetivo y el método es vital para la defensa proactiva.

## 🔍 Módulo: Gestión de Vulnerabilidades (CVE y CVSS)

### Conceptos Clave
- **CVE:** El diccionario universal de vulnerabilidades de la industria (Formato: `CVE-AÑO-NÚMERO`).
- **CVSS:** Sistema de puntuación del 0 al 10 que define la gravedad de un fallo de seguridad. Permite al Blue Team priorizar los riesgos.
- **PoC (Prueba de Concepto):** Scripts públicos que demuestran cómo explotar una vulnerabilidad específica.

## 🐧 Fundamentos de Linux y Bash (`Terminal Intro`)

### Comandos de Identidad y Salida
- **`whoami`:** Muestra el nombre del usuario actual en el sistema. Crucial para verificar privilegios antes de ejecutar herramientas de red.
- **`echo`:** Imprime texto en la terminal. 
  - *Uso simple:* `echo TryHackMe`
  - *Uso con múltiples palabras:* `echo "Hello World"` (requiere comillas).
 
  - ### Comandos de Navegación Esenciales
- **`pwd`:** Imprime el directorio de trabajo actual (¿Dónde estoy parado?).
- **`ls`:** Lista los archivos y carpetas del directorio actual (las carpetas se ven azules).
- **`cd [carpeta]`:** Cambia de directorio. `cd ..` sirve para retroceder un nivel.
- **`cat [archivo]`:** Muestra el contenido completo de un archivo en la terminal.

### Comandos de Búsqueda y Filtrado (Análisis de Logs)
- **`find -name [archivo]`:** Busca archivos por su nombre exacto en el sistema.
  - *Ejemplo:* `find -name passwords.txt`
- **`grep "[texto]" [archivo]`:** Busca y extrae cadenas de texto específicas dentro de un archivo. Es fundamental en el Blue Team para analizar archivos de logs gigantescos.
  - *Ejemplo:* `grep "THM" access.log`

### Operadores y Redireccionadores en Bash
- **`&`:** Ejecuta un comando en segundo plano (*background*) para poder seguir usando la terminal.
- **`&&`:** Ejecuta dos comandos en cadena, esperando que el primero termine con éxito antes de iniciar el segundo.
- **`>`:** Redirecciona la salida de un comando hacia un archivo, **sobrescribiendo** todo su contenido.
- **`>>`:** Redirecciona la salida hacia un archivo, **añadiendo** el texto al final sin borrar lo existente.




