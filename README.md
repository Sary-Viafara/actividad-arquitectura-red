# Actividad-1-Arquitectura-de-Red
Trabajo en equipo desarrollado con Zuelem Chanillao, Natalia Medel, Sary Viafara y Alexander Hass

# Modelo OSI, IP Subred, DNS  

---

## 🧩 1. Conceptos base  

Completar tabla:  


| Concepto | Definición simple | Nivel técnico breve | Ejemplo real |
|----------|------------------|--------------------|--------------|
| Modelo OSI | Es una forma de entender cómo viaja la información correctamente en internet en pasos o capas. | Modelo de referencia que estandariza funciones de red en capas. | Cuando mandas un mensaje por WhatsApp pasa por varias capas antes de llegar a su destino. |
| Subred (Subnet) | División dentro de una red, como separar una casa en habitaciones para organizar mejor. | Divide una red usando máscaras IP para organizar mejor el tráfico. | Red WiFi de tu casa separada de la red de invitados. |
| DNS | Es como una agenda que traduce nombres de páginas webs a direcciones IP. | Sistema que convierte dominios (google.com) en IP (142.x.x.x). | Escribes google.com y te lleva al sitio sin saber la IP. |

---

## 🧱 2. Modelo OSI  

### ¿Qué es el modelo OSI?  

Es un modelo que explica cómo se comunican los sistemas en red en 7 pasos (capas).  

### ¿Para qué sirve?  

Sirve para entender, diseñar y solucionar problemas en redes (debuggear más fácil).  

### Tabla de capas  

| Capa | Nombre | ¿Qué hace? |
|------|--------|-----------|
| 1 | Física | Envía bits (señales eléctricas, cables, WiFi). |
| 2 | Enlace | Conecta dispositivos en la misma red (MAC). |
| 3 | Red | Encuentra la ruta usando IP. |
| 4 | Transporte | Asegura que los datos lleguen completos (TCP/UDP). |
| 5 | Sesión | Mantiene la conexión activa entre sistemas. |
| 6 | Presentación | Traduce datos (ej: cifrado, formatos). |
| 7 | Aplicación | Interacción directa con el usuario (web, apps). |

👉 Idea clave: los datos bajan por capas al enviar y suben al recibir .  

---

## 🌐 3. DNS (lo que usas todos los días)  

### ✅ ¿Qué es DNS?  

DNS significa Domain Name System (Sistema de Nombres de Dominio).  

👉 Es básicamente la agenda de internet.  

Tú escribes: google.com  

DNS lo traduce a algo como: 142.250.190.78 (una IP)  

📌 En simple: DNS convierte nombres fáciles de recordar en direcciones que las máquinas entienden.  

---

### ❓ ¿Por qué no usamos IP directamente?  

En vez de google.com → tendrías que escribir 142.250.190.78  

Y memorizar cientos de números para cada sitio  

👉 Problemas de usar IP:  

Difícil de recordar  
Las IP pueden cambiar  
Un sitio puede tener muchas IPs  

👉 En cambio: Un dominio (como google.com) estable y fácil para humanos.  

---

### 🔄 ¿Qué pasa cuando escribes google.com en el navegador?  

Paso 1: Escribes la URL: Tú escribes: google.com  

Paso 2: Tu computadora pregunta “¿cuál es la IP?” Tu equipo dice: “Necesito saber la IP de google.com”  

Paso 3: Consulta al DNS  

Va a un servidor DNS (como el de tu internet o uno público tipo Google DNS).  

Básicamente pregunta: “¿Cuál es la IP de google.com?”  

Paso 4: El DNS responde con la IP: El DNS devuelve algo como: 142.250.190.78  

Paso 5: Se conecta al servidor: Tu navegador ahora sí puede: Ir a esa IP y pedir: “Dame la página de google”  

---

### 🎯 Flujo completo  

Usuario → DNS → obtiene IP → servidor responde → ves la web  

---

### 💡 Analogía simple  

DNS = agenda de contactos  
Dominio = nombre (“Google”)  
IP = número de teléfono  

---

## 🧩 4. Subnets (subredes)  

### ✅ ¿Qué es una subred?  

Una red es un grupo de dispositivos conectados (ej: Todos conectados a un Wifi: eso es una red).  

Una subred (subnet) es un grupo más pequeño dentro de una red grande.  

(Ejemplo: El edificio completo = la red; Cada piso = una subred)  

---

### 🎯 ¿Para qué sirve?  

- Organizar mejor la red (separa cosas por función)  

- Mejorar seguridad 🔒 (Puedes separar Invitados (WiFi visitas) de tus dispositivos personales, así los invitados NO acceden a tus cosas)  
- Evitar tráfico innecesario 🚗 (menos ruido en la red = todo más rápido)  

- Facilitar el control  

---

### ❓ ¿Por qué dividir redes?  

Porque una red grande sin orden es un desastre:  

❌ Sin subredes:  

- Todos los dispositivos “gritan” en la misma red  
- Más lentitud  
- Más difícil de administrar  
- Menos seguridad  

---

### ✅ Con subredes:  

- Separas áreas  
- Controlas quién habla con quién  
- Mejor rendimiento  

---

### 💡 Ejemplo simple  

Imagina una empresa:  

Sin subredes:  

- Todos los computadores en la misma red  
- Finanzas, desarrollo, invitados → TODO mezclado  

Con subredes:  

- Subred 1: Finanzas 💰  
- Subred 2: Desarrollo 👨‍💻  
- Subred 3: Invitados 📶  

👉 Así:  

- Finanzas no se mezcla con invitados  
- Más seguridad  
- Mejor control  

---

### 👨‍💻 Ejemplo developer (muy importante)  

1. Red local (tu casa)  

- IPs tipo: 192.168.1.x  
- Todos tus dispositivos en la misma subred  

👉 Ej: (Laptop, Celular, Smart TV)  

---

2. Red en cloud (ej: AWS, Azure, etc.)  

Aquí SIEMPRE se usan subredes.  

Ejemplo típico:  

- Subred pública 🌍  
Servidores web (accesibles desde internet)  

- Subred privada 🔒  
Bases de datos  
APIs internas  

---

### 🏗️ Ejemplo real de arquitectura  

Internet  

↓  

[Servidor Web]  → Subred pública  

↓  

[Backend API]   → Subred privada  

↓  

[Base de datos] → Subred privada más segura  

---

### 🧠 Resumen corto  

DNS:  

- Traduce nombres → IP  
- Hace que internet sea usable para humanos  

Subnets:  

- Dividen redes grandes en pequeñas  
- Mejoran seguridad, orden y rendimiento  

---

## 💻 5. Conexión directa con desarrollo  

Cuando tu app falla al conectarse, normalmente el problema ocurre en una de estas 3 capas: DNS → IP → Red.  

---

### ¿Qué pasa cuando tu app No encuentra el servidor?  

### 1) Si no encuentra el servidor la capa afectada es la Red / Conectividad. 
La app ya sabe a qué IP ir, pero no logra llegar al servidor.  

Causas comunes:  

- Servidor caído  
- Puerto cerrado  
- Firewall bloqueando  
- Backend no está escuchando  

---

### 2) ¿Qué pasa cuando tu app No resuelve el dominio?  

No resuelve el dominio, la capa afectada es DNS.  

El dominio (ej: api.midominio.com) no se traduce a una IP.  

Causas comunes:  

- DNS mal configurado  
- Dominio expirado  
- Propagación DNS incompleta  
- Error en registros A / CNAME  

---

### 3) ¿Qué pasa cuando tu app no puede conectarse?  

La capa afectada es Red / Transporte.  

Esto quiere decir que se resolvió el dominio → hay IP → pero la conexión falla  

Causas comunes:  

- Timeout  
- Puerto incorrecto  
- HTTPS mal configurado  
- Certificado inválido  
- Backend no responde  

---

## 🚨 6. Problemas reales (debugging)  

### ¿Qué significa: “DNS not found”?  

Significa que hay una falla en el DNS  

Significa: El dominio no existe o no puede resolverse  

Ejemplo:  
GET https://api.loquesea.com → DNS error  

Qué revisar:  

- ¿El dominio está bien escrito?  
- ¿Existe el registro DNS?  
- ¿Propagación DNS completada?  

---

### ¿Qué significa: “Host unreachable”?  

Hay una falla de red (routing)  

Significa: No hay ruta hacia el servidor (ni siquiera llega)  

Causas:  

IP incorrecta  
Servidor apagado  
Problema en red/intermediarios  

Qué revisar:  

- ping  
- traceroute  
- Estado del servidor (cloud / VM)  

---

### ¿Qué significa: “Network error”?  

Hay un error genérico en la red (frontend/backend)  

Significa que la request falló pero sin detalle claro  

Causas típicas:  

CORS bloqueado  
Timeout  
SSL/TLS error  
Backend caído  

Qué revisar:  

- Consola del navegador  
- Network tab (status code)  
- Logs del backend  
- Configuración CORS  

---

### ¿Qué revisarías primero como developer?  

DNS → Red → Servidor → Aplicación  

La revisaría en ese orden, porque cada capa depende de la anterior.  

---

## 🌍 7. Caso práctico real  

Escenario:  

“Tu aplicación está deployada, pero nadie puede acceder”  

Responder:  

- ¿Es problema de DNS?  
- ¿Es problema de red?  
- ¿Es problema de configuración?  

---

## 🧪 8. Analogía obligatoria  

| Concepto | Analogía |
|----------|---------|
| Modelo OSI | Es como una cocina profesional: cada estación (preparación, cocción, emplatado) tiene un rol específico hasta que el plato llega al cliente. |
| DNS | Es como preguntarle a recepción en un hotel por una persona: dices el nombre y te indican la habitación exacta. |
| Subnet (Subred) | Es como separar un colegio en salas por curso: cada grupo trabaja en su espacio para evitar desorden y mejorar la organización. |

👉 Ejemplo esperado:  

- OSI = proceso de envío de paquete paso a paso  
- DNS = agenda de contactos  
- Subnet = barrios dentro de una ciudad  

---

## 🧠 BONUS (Nivel Bootcamp Pro)  

### ¿Qué es un VPC en cloud?  

Es una red virtual aislada y segura dentro de una nube pública (como AWS, Google Cloud o Azure).  

Permite a las empresas tener su propio espacio privado, con control total sobre:  
- Direcciones IP  
- Subredes  
- Tablas de rutas  
- Firewalls  

Ofrece la escalabilidad de la nube pública con la seguridad de una red privada.  

---

### ¿Qué es una IP privada vs pública?  

La IP pública es única en internet y la asigna tu proveedor (ISP) para identificar tu hogar/empresa globalmente.  

La IP privada la asigna tu router para identificar cada dispositivo (móvil, PC) dentro de tu red local.  

---

### ¿Qué es un load balancer?  

Es un dispositivo físico, software o servicio en la nube que distribuye eficientemente el tráfico de red o las aplicaciones entre múltiples servidores.  

Su objetivo principal es:  

- Optimizar el rendimiento  
- Garantizar la alta disponibilidad  
- Evitar la sobrecarga de un solo servidor  
- Mejorar la experiencia del usuario  
