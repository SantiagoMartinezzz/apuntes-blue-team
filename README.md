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



