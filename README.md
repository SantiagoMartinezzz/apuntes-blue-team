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

