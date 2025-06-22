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


### Estado actual de TransChile (flujo desorganizado)

![Editor _ Mermaid Chart-2025-06-22-231156](https://github.com/user-attachments/assets/b37664c6-4381-43fb-961a-97c0d3d72937)
   
---
### 1.2 Problemas más críticos

- Sin repositorio central ni versiones trazables.
- Sin pruebas ni integración continua.
- Vulnerabilidades por paquetes no auditados.
- Código de baja calidad y errores frecuentes en producción.

### 1.3 Impacto de la situación actual

- 🚨 Demoras operativas y errores logísticos.
- ⌛ Pérdida de tiempo en resolución de errores evitables.
- 🔓 Mayor riesgo de ataques y fallos en producción.
- 📉 Falta de confianza en la entrega continua del software.

---

## 🔁 2. Propuesta de implementación de Git y control de versiones

### 2.1 Comparación de flujos de trabajo

| Flujo | Ventajas | Desventajas |
|-------|----------|-------------|
| **Git Flow** | Ideal para versiones planificadas, controlado | Complejo para equipos pequeños |
| **GitHub Flow** | Ligero, perfecto para entregas continuas | Requiere buena gestión de PRs |
| **Trunk-based Development** | Flujo simple, fomenta CI diaria | Requiere commits pequeños frecuentes |

### 2.2 Propuesta: Git + GitHub Flow

Se recomienda implementar **Git con GitHub Flow**, ideal para equipos que hacen entregas frecuentes y necesitan fluidez.

### 2.3 Justificación

- 🤝 Facilita la colaboración y revisión.
- 🔄 Compatible con integración continua.
- 🧾 Proporciona trazabilidad y control.

---

## ⚙️ 3. Implementación de integración continua

### 3.1 Herramienta propuesta: GitHub Actions

- 🔗 Integración nativa con GitHub
- 💸 Gratis para proyectos públicos
- 🧩 YAML flexible para definir flujos

### 3.2 Pipeline de CI/CD propuesto

```yaml
name: CI Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-test-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Configurar JDK
        uses: actions/setup-java@v3
        with:
          java-version: '17'
      - name: Compilar proyecto
        run: mvn clean compile
      - name: Ejecutar pruebas
        run: mvn test
      - name: Analizar calidad con SonarQube
        run: mvn sonar:sonar
      - name: Despliegue (simulado)
        run: echo "Desplegando a servidor de pruebas..."

---

### 3.3 Estrategias de calidad

- ✔️ **Pruebas automáticas obligatorias antes del merge**
- 🎯 **Cobertura mínima del 80%** para aprobación
- 🔐 **Integración con SonarQube y Dependabot** para análisis continuo y actualizaciones seguras

---

## 🔒 4. Seguridad y análisis estático

### 4.1 SonarQube

- 🔍 Detección de vulnerabilidades, errores y código duplicado
- 🧠 Reportes automáticos en cada `push` a la rama `main`
- 🛑 Posibilidad de **bloquear despliegues** si hay fallas críticas

### 4.2 Infraestructura segura

- 👤 Gestión de **roles y permisos** en GitHub
- 🔑 Uso de **claves SSH** en procesos de despliegue
- 📋 **Auditorías** de cambios y trazabilidad del código

### 4.3 Prevención de paquetes inseguros

- 📦 **Dependabot activado** para monitoreo de dependencias
- 🧪 Validación previa de nuevas bibliotecas y versiones
- 📁 Archivo `SECURITY.md` para documentar políticas de seguridad y fuentes confiables

---

## 📌 Conclusiones

La empresa **TransChile** debe modernizar su flujo de desarrollo adoptando herramientas y metodologías clave:

- ✅ **Git y GitHub Flow** para control de versiones
- ✅ **GitHub Actions** para automatización y CI/CD
- ✅ **SonarQube** para control de calidad y seguridad
- ✅ Herramientas de **prevención de errores y ciberataques**

Esto asegurará un software más **seguro**, **confiable** y **ágil**, mejorando sustancialmente toda la operación logística.

