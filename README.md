# 🚚 Sistema de Gestión de Ventas y Despachos — DevOps Deployment Project

Proyecto académico desarrollado para la evaluación EV2 de Herramientas DevOps, enfocado en la contenedorización, despliegue automatizado y ejecución distribuida de microservicios utilizando Docker, GitHub Actions y AWS EC2.

---

# 📌 Descripción del Proyecto

La solución implementa una arquitectura basada en microservicios compuesta por:

- Frontend React
- API de Ventas (Spring Boot)
- API de Despachos (Spring Boot)
- Base de datos MariaDB
- Contenedores Docker
- Automatización CI/CD con GitHub Actions
- Despliegue en AWS EC2

El objetivo principal fue construir un entorno completamente contenerizado, automatizado y preparado para despliegues continuos siguiendo principios DevOps.

---

# 🏗️ Arquitectura de la Solución

```text
                    ┌────────────────────┐
                    │     Frontend       │
                    │ React + Docker     │
                    │  EC2 Pública       │
                    └─────────┬──────────┘
                              │
                              ▼
          ┌──────────────────────────────────┐
          │        Backend Privado           │
          │                                  │
          │  ┌──────────────────────────┐    │
          │  │      Ventas API          │    │
          │  │ Spring Boot + Docker     │    │
          │  └─────────────┬────────────┘    │
          │                │                 │
          │  ┌─────────────▼────────────┐    │
          │  │     Despacho API         │    │
          │  │ Spring Boot + Docker     │    │
          │  └─────────────┬────────────┘    │
          │                │                 │
          │        ┌───────▼───────┐         │
          │        │   MariaDB     │         │
          │        │ Docker Volume │         │
          │        └───────────────┘         │
          └──────────────────────────────────┘
```

---

# 🚀 Tecnologías Utilizadas

| Tecnología | Uso |
|---|---|
| React | Frontend |
| Spring Boot | Backend APIs |
| MariaDB | Base de datos |
| Docker | Contenedorización |
| Docker Compose | Orquestación local |
| GitHub Actions | CI/CD |
| AWS EC2 | Infraestructura cloud |
| Docker Hub | Registro de imágenes |
| Git | Control de versiones |

---

# 📂 Estructura del Proyecto

```text
├── back-Despachos_SpringBoot/
├── back-Ventas_SpringBoot/
├── front_despacho/
├── docker-compose.yml
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml
```

---

# 🐳 Contenedorización

Cada servicio fue dockerizado utilizando buenas prácticas DevOps:

✅ Multi-stage build  
✅ Imágenes optimizadas  
✅ Separación Frontend / Backend  
✅ Variables de entorno  
✅ Redes Docker  
✅ Persistencia con volúmenes  
✅ Despliegue independiente por servicio  

---

# ⚙️ Docker Compose

El sistema utiliza `docker-compose.yml` para levantar:

- Frontend
- Ventas API
- Despacho API
- MariaDB

## Levantar entorno completo

```bash
docker compose up -d
```

## Ver contenedores activos

```bash
docker ps
```

## Detener entorno

```bash
docker compose down
```

---

# 💾 Persistencia de Datos

La persistencia fue implementada mediante Docker Volumes sobre MariaDB.

## Justificación técnica

Se utilizó un volumen persistente para asegurar:

- Continuidad operativa
- Persistencia tras reinicios
- Separación entre contenedor y datos
- Mantenibilidad del entorno

Esto permite que la información almacenada en la base de datos no se pierda aunque los contenedores sean recreados.

---

# ☁️ Infraestructura AWS

La solución fue desplegada utilizando instancias EC2 separadas:

| Servicio | Tipo |
|---|---|
| Frontend | EC2 Pública |
| Backend APIs | EC2 Privada |
| Base de datos | Docker Container |

## Seguridad implementada

- Frontend accesible desde Internet
- Backend restringido mediante Security Groups
- Comunicación interna controlada
- APIs privadas protegidas

---

# 🔄 Pipeline CI/CD

El proyecto implementa integración y despliegue continuo mediante GitHub Actions.

## Flujo automatizado

```text
Push rama deploy
        ↓
GitHub Actions
        ↓
Build imágenes Docker
        ↓
Push Docker Hub
        ↓
Actualización de imágenes desplegadas
```

## Características del pipeline

✅ Trigger automático en rama `deploy`  
✅ Build automático  
✅ Push automático a Docker Hub  
✅ Uso de GitHub Secrets  
✅ Automatización de distribución de imágenes  

---

# 🔐 GitHub Secrets

Se utilizaron secrets para proteger:

- Docker Username
- Docker Password
- Variables sensibles

Esto evita exponer credenciales dentro del repositorio.

---

# 🌐 Docker Hub

Imágenes publicadas:

- `frontend-app`
- `ventas-api`
- `despacho-api`

Repositorio Docker Hub:

```text
https://hub.docker.com/
```

---

# 📸 Evidencias del Proyecto

## Funcionalidades demostradas

✅ Frontend accesible desde navegador  
✅ APIs funcionando correctamente  
✅ Comunicación Front → Back  
✅ Persistencia de datos  
✅ Contenedores Docker operativos  
✅ GitHub Actions funcional  
✅ Integración completa en AWS EC2  

---

# 🧪 Validaciones Realizadas

## Backend

```bash
curl http://localhost:8081/api/v1/ventas
curl http://localhost:8082/api/v1/despachos
```

## Docker

```bash
docker ps
docker logs <container>
```

## Frontend

- Validación mediante navegador
- Verificación Network / API Calls
- Consumo correcto de endpoints

---

# 📈 Principios DevOps Aplicados

Este proyecto implementa prácticas reales DevOps:

- Contenedorización
- Automatización
- Integración continua
- Despliegue continuo
- Persistencia de datos
- Infraestructura cloud
- Gestión de entornos
- Seguridad de servicios
- Escalabilidad
- Trazabilidad

---

# 🎯 Resultados Obtenidos

✅ Plataforma completamente contenerizada  
✅ Frontend y Backend desplegados exitosamente  
✅ Comunicación estable entre servicios  
✅ Persistencia funcional  
✅ Pipeline CI/CD operativo  
✅ Automatización de distribución Docker  
✅ Arquitectura lista para escalamiento futuro  

---

# 👨‍💻 Autores

Proyecto desarrollado para EV2 — Herramientas DevOps.

- Sebastián Carrera Ortiz
- Integrante Dupla

---

# 📚 Consideraciones Finales

La solución fue diseñada siguiendo principios modernos de desarrollo y despliegue cloud-native, permitiendo:

- Escalabilidad
- Portabilidad
- Mantenibilidad
- Automatización
- Seguridad
- Facilidad de despliegue

El proyecto demuestra la aplicación práctica de herramientas DevOps modernas sobre infraestructura AWS utilizando Docker y GitHub Actions.