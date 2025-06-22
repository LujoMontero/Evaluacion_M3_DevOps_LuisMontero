# 🛠️ Integración Continua en TransChile - Evaluación DevOps M3

## 🚚 Contexto de la Empresa

***TransChile*** desarrolla su software de manera artesanal y desorganizada. No utilizan control de versiones, y los desarrolladores trabajan de forma aislada. El código se integra manualmente una vez al mes y se sube al servidor por FTP, sin validación ni pruebas automatizadas. Esto resulta en un entorno de desarrollo frágil, propenso a errores en producción y a vulnerabilidades de seguridad.

---
## 🔍 Análisis del Estado Actual

### Problemas Detectados

- ❌ **Falta de control de versiones:** sin repositorio central, los desarrolladores trabajan en archivos locales y sincronizan el código manualmente una vez al mes.
- ❌ **Sin CI/CD:** no utilizan Jenkins, GitHub Actions ni GitLab CI/CD; no se ejecutan pruebas automáticas.
- ❌ **Problemas de seguridad:** uso de paquetes inseguros sin auditoría ni análisis estático.
- ❌ **Código de baja calidad:** sin herramientas como SonarQube ni revisiones formales.
- ❌ **Flujo de trabajo ineficiente:** cada desarrollador sube código sin revisión, sin metodología como Git Flow o Trunk-based Development.


### M3-R1: Estado actual de TransChile (flujo desorganizado)

gitGraph
   commit id: "Desarrollador 1 crea archivo local"
   commit id: "Desarrollador 2 crea archivo local"
   branch dev1
   checkout dev1
   commit id: "Cambios locales sin control"
   branch dev2
   checkout dev2
   commit id: "Modificaciones sin pruebas"
   checkout main
   commit id: "Unión manual del código (FTP)"
   commit id: "Errores en producción"
   commit id: "Parche rápido sin validación"

   
---

## ✅ Propuesta Técnica
