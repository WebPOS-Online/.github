<div align="center">

<img src="https://raw.githubusercontent.com/webpos-onlline/.github/profile/logo.png" alt="WebPOS Online" width="120" />

# 🧾 WebPOS Online

### ☁️ Software comercial en la nube para el retail y la facturación electrónica en Latinoamérica

<br/>

[![Panamá](https://img.shields.io/badge/🇵🇦_Panamá-DGI-005293?style=for-the-badge&labelColor=1a1a1a)](#-referencias-fiscales-oficiales)
[![República Dominicana](https://img.shields.io/badge/🇩🇴_Rep._Dominicana-DGII-002D62?style=for-the-badge&labelColor=1a1a1a)](#-referencias-fiscales-oficiales)
[![Costa Rica](https://img.shields.io/badge/🇨🇷_Costa_Rica-Hacienda-C8102E?style=for-the-badge&labelColor=1a1a1a)](#-referencias-fiscales-oficiales)

<br/>

![Repos](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Forgs%2Fwebpos-onlline&query=%24.public_repos&label=repositorios&style=flat-square&color=6366f1&logo=github)
![C#](https://img.shields.io/badge/C%23-512BD4?style=flat-square&logo=csharp&logoColor=white)
![.NET](https://img.shields.io/badge/.NET-8%20%7C%2010-512BD4?style=flat-square&logo=dotnet&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-20-DD0031?style=flat-square&logo=angular&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-Service_Bus-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

</div>

<div align="center">

```
─────────────────────────────────────────────────────────────
   POS en la nube  ·  Facturación electrónica  ·  Multipaís
─────────────────────────────────────────────────────────────
```

</div>

---

## 🎯 ¿Qué hacemos?

Construimos y operamos una **plataforma de punto de venta en la nube** junto con todo el
ecosistema de servicios que la rodea: APIs de negocio, agentes de facturación
electrónica, portales de consulta para clientes y herramientas internas de
soporte y administración.

<table>
<tr>
<td width="33%" valign="top">

### 🛒 Punto de venta & APIs

WebPOS y su capa de servicios: ventas, inventario, cierres de caja e integraciones con terceros.

</td>
<td width="33%" valign="top">

### 🧾 Facturación electrónica

Firmado, encolado, envío y consulta de documentos fiscales ante **DGI** 🇵🇦, **DGII** 🇩🇴 y **Hacienda** 🇨🇷.

</td>
<td width="33%" valign="top">

### 🛠️ Herramientas internas

Backoffice, portal de soporte y automatización de despliegues para un equipo pequeño que atiende varios países.

</td>
</tr>
</table>

> [!NOTE]
> 🌎 Cada producto se despliega bajo **configuración por país**: catálogos fiscales,
> plantillas, reglas de validación y archivos de traducción JSON independientes por mercado.
> Nada se codifica para un solo país.

---

## 🗺️ Arquitectura en un vistazo

```mermaid
flowchart LR
    subgraph Cliente["🖥️  Cliente"]
        POS["🛒 WebPOS"]
        PFE["🌐 Portal FE"]
    end

    subgraph Servicios["⚙️  Servicios"]
        API["🔌 WebPOSApis"]
        SRV["📦 WPServer"]
    end

    subgraph FE["🧾  Facturación Electrónica"]
        AGT["🤖 feAgent"]
        QUE["📨 WPAzQueueProc"]
    end

    subgraph Fisco["🏛️  Autoridades fiscales"]
        DGI["🇵🇦 DGI"]
        DGII["🇩🇴 DGII"]
        HAC["🇨🇷 Hacienda"]
    end

    POS --> API
    PFE --> API
    API --> SRV
    API --> AGT
    AGT --> QUE
    QUE --> DGI & DGII & HAC
```

---

## 📚 Repositorios

### 🏛️ Núcleo del producto

| | Repositorio | Descripción | Stack |
|:--:|---|---|---|
| 🛒 | **[`WebPOS`](https://github.com/webpos-onlline/WebPOS)** | Aplicación de punto de venta en la nube. Incluye el portal **FFO** de documentos fiscales. | ![](https://img.shields.io/badge/ASP.NET_4.8-512BD4?style=flat-square&logo=dotnet&logoColor=white) ![](https://img.shields.io/badge/AngularJS-B52E31?style=flat-square&logo=angularjs&logoColor=white) ![](https://img.shields.io/badge/EF6-512BD4?style=flat-square) |
| 🔌 | **[`WebPOSApis`](https://github.com/webpos-onlline/WebPOSApis)** | Capa de APIs de negocio. Manejo centralizado de errores con `DelegatingHandler`, `ApiExceptionFilter` y patrón *Result Wrapper*. | ![](https://img.shields.io/badge/Web_API_4.8_(x86)-512BD4?style=flat-square&logo=dotnet&logoColor=white) ![](https://img.shields.io/badge/EF6-512BD4?style=flat-square) |
| 📦 | **[`WPServer`](https://github.com/webpos-onlline/WPServer)** | Servidor de recursos y despliegue de assets por país: plantillas HTML, controladores JS, CSS y traducciones JSON. | ![](https://img.shields.io/badge/IIS-262626?style=flat-square&logo=microsoft&logoColor=white) ![](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| 🌐 | **[`WPPortalFE`](https://github.com/webpos-onlline/WPPortalFE)** | Front-end del Portal FE. Consume `WebPOSApis`. CI/CD con GitHub Actions y publicación de artefactos a SharePoint vía Microsoft Graph. | ![](https://img.shields.io/badge/AngularJS-B52E31?style=flat-square&logo=angularjs&logoColor=white) ![](https://img.shields.io/badge/MSBuild-2560E0?style=flat-square&logo=githubactions&logoColor=white) |

<br/>

### 🧾 Facturación electrónica

| | Repositorio | Descripción | Stack |
|:--:|---|---|---|
| 🤖 | **[`WPAgent`](https://github.com/webpos-onlline/WPAgent)** · **[`feAgent`](https://github.com/webpos-onlline/feAgent)** | Agente de facturación electrónica: emisión, consulta, **descarga masiva de PDF/XML** y reenvío de correos. Multipaís 🇵🇦 🇩🇴 🇨🇷. | ![](https://img.shields.io/badge/C%23-512BD4?style=flat-square&logo=csharp&logoColor=white) ![](https://img.shields.io/badge/.NET_4.8-512BD4?style=flat-square&logo=dotnet&logoColor=white) |
| 📨 | **[`WPAzQueueProc`](https://github.com/webpos-onlline/WPAzQueueProc)** | Dispatcher CLI para el procesamiento de colas de facturación electrónica sobre Azure Service Bus / MSMQ. | ![](https://img.shields.io/badge/Azure_Service_Bus-0078D4?style=flat-square&logo=microsoftazure&logoColor=white) ![](https://img.shields.io/badge/MSMQ-262626?style=flat-square&logo=microsoft&logoColor=white) |

<details>
<summary><b>🔄 Migración en curso — del pipeline MSMQ a Azure Service Bus</b></summary>

<br/>

El pipeline `FFO → MSMQ → servicio de Windows → DGI` se está migrando a **Azure Service Bus**
con un enfoque **strangler fig**, resolviendo los cuellos de botella históricos de la cola
y los bloqueos del servicio.

**Máquina de estados explícita:**

```mermaid
stateDiagram-v2
    [*] --> Creado
    Creado --> Firmado
    Firmado --> Encolado
    Encolado --> EnProceso
    EnProceso --> EnviadoSinAcuse
    EnviadoSinAcuse --> Reintentando
    Reintentando --> EnProceso
    EnProceso --> Aceptado
    EnProceso --> Rechazado
    Reintentando --> Cuarentena
    Aceptado --> [*]
    Rechazado --> [*]
    Cuarentena --> [*]
```

| ✅ | Garantía de diseño |
|:--:|---|
| 🔐 | Transiciones **write-ahead** con `UPDATE` guardados para concurrencia segura |
| 🔑 | Claves de **idempotencia deterministas** |
| 🧹 | Trabajos separados de **reaper** y **reconciler** |
| ⚡ | SQL directo sobre el *change tracker* de EF6 donde la precisión importa |

</details>

<br/>

### 🚀 Plataformas nuevas

| | Repositorio | Descripción | Stack |
|:--:|---|---|---|
| 🏢 | **[`WPBackOffice`](https://github.com/webpos-onlline/WPBackOffice)** | Backoffice interno. Envuelve las BLL legadas (.NET 4.8) mediante una capa adaptadora con **Clean Architecture**. | ![](https://img.shields.io/badge/Blazor_Server-512BD4?style=flat-square&logo=blazor&logoColor=white) ![](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) ![](https://img.shields.io/badge/Entra_ID-0078D4?style=flat-square&logo=microsoft&logoColor=white) |
| 🎫 | **[`support-portal`](https://github.com/webpos-onlline/support-portal)** | Portal de soporte multipaís. Dos apps Angular (`portal-public` y `admin`), middleware de contexto por país y auth JWT de agentes. | ![](https://img.shields.io/badge/.NET_10-512BD4?style=flat-square&logo=dotnet&logoColor=white) ![](https://img.shields.io/badge/Angular_20-DD0031?style=flat-square&logo=angular&logoColor=white) ![](https://img.shields.io/badge/PostgreSQL_16-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![](https://img.shields.io/badge/MinIO-C72E49?style=flat-square&logo=minio&logoColor=white) |
| 🧠 | **[`AgentOS`](https://github.com/webpos-onlline/AgentOS)** | Plataforma de agentes de IA para dispositivos **edge** (Raspberry Pi) en local del cliente. Agentes verticales descargables y licenciamiento por hardware (CPU/MAC/TPM). | ![](https://img.shields.io/badge/.NET-512BD4?style=flat-square&logo=dotnet&logoColor=white) ![](https://img.shields.io/badge/Raspberry_Pi-A22846?style=flat-square&logo=raspberrypi&logoColor=white) ![](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) |

---

## 🧰 Stack tecnológico

<div align="center">

**⚙️ Back-end**

![C#](https://img.shields.io/badge/C%23-512BD4?style=for-the-badge&logo=csharp&logoColor=white)
![.NET](https://img.shields.io/badge/.NET_Framework_4.8-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![.NET 10](https://img.shields.io/badge/.NET_8_|_10-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![EF](https://img.shields.io/badge/EF6_/_EF_Core-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)

**🎨 Front-end**

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Angular](https://img.shields.io/badge/Angular_20-DD0031?style=for-the-badge&logo=angular&logoColor=white)
![AngularJS](https://img.shields.io/badge/AngularJS-B52E31?style=for-the-badge&logo=angularjs&logoColor=white)
![Blazor](https://img.shields.io/badge/Blazor-512BD4?style=for-the-badge&logo=blazor&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)

**🗄️ Datos & mensajería**

![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL_16-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![MinIO](https://img.shields.io/badge/MinIO-C72E49?style=for-the-badge&logo=minio&logoColor=white)
![Azure](https://img.shields.io/badge/Service_Bus-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)

**🚢 Infra & CI/CD**

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Docker](https://img.shields.io/badge/Docker_Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![IIS](https://img.shields.io/badge/IIS-262626?style=for-the-badge&logo=microsoft&logoColor=white)
![Oracle Cloud](https://img.shields.io/badge/Oracle_Cloud_ARM64-F80000?style=for-the-badge&logo=oracle&logoColor=white)

</div>

---

## 🤝 Cómo trabajamos

| | Práctica | Detalle |
|:--:|---|---|
| 🌿 | **Git Flow simplificado** | Ramas `feature/*`, `release/*`, `hotfix/*` sobre `develop` y `main` |
| 📝 | **Conventional Commits** | `feat:` · `fix:` · `refactor:` · `docs:` · `chore:` |
| 👀 | **Revisión por PR** | Obligatoria antes de integrar. Sin merge directo a `develop` |
| 🔀 | **Rebase antes de integrar** | Historial lineal y legible |
| 🌎 | **Configuración por país** | Ciudadano de primera clase, no un parche |
| 🧬 | **Migración incremental** | Estrangulamos lo legado en vez de reescribirlo de cero |

---

## 🔗 Enlaces de interés

| | Recurso | |
|:--:|---|---|
| 📖 | **Documentación técnica interna** | [Wiki de la organización](https://github.com/webpos-onlline/WebPOS/wiki) |
| 📐 | **Convenciones de Git y PR** | [`CONTRIBUTING.md`](https://github.com/webpos-onlline/.github/blob/main/CONTRIBUTING.md) |
| 🗂️ | **Tableros de trabajo** | [GitHub Projects](https://github.com/orgs/webpos-onlline/projects) |
| 🎫 | **Reporte de incidencias** | Portal de soporte (`support-portal`) |
| 👥 | **Equipos** | [Teams](https://github.com/orgs/webpos-onlline/teams) |

### 🏛️ Referencias fiscales oficiales

| | País | Entidad | Enlace |
|:--:|---|---|---|
| 🇵🇦 | Panamá | Dirección General de Ingresos | [dgi.mef.gob.pa](https://dgi.mef.gob.pa/) |
| 🇩🇴 | República Dominicana | DGII — e-CF | [dgii.gov.do](https://dgii.gov.do/) |
| 🇨🇷 | Costa Rica | Ministerio de Hacienda | [hacienda.go.cr](https://www.hacienda.go.cr/) |

---

<div align="center">

```
🇵🇦  ·  🇩🇴  ·  🇨🇷
```

**WebPOS Online**

<sub>Hecho con ☕ y C# desde Latinoamérica</sub>

</div>
