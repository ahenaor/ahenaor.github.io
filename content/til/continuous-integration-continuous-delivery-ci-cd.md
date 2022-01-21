---
author: 'Alejo Henao'
title: 'Qué es CI/CD - Continuous Integration (CI) / Continuous Delivery (CD)'
date: '2021-01-21'
description: 'Este artículo describe a grandes rasgos el concepto de CI/CD - Continuous Integration (CI) / Continuous Delivery (CD).'
tags: ['CI/CD', 'CI', 'CD', 'Continuous Integration', 'Continuous Delivery', 'Integración Continua', 'Despliegue Continuo']
categories: ['Conceptos']
series: ['DevOps']
aliases: ['CI-CD-continuous-integration-continuous-delivery']
ShowToc: false
TocOpen: false
hideSummary: false

---

De manera general, **CI/CD** es un concepto de ingeniería de software que hace referencia a las prácticas combinadas de **Continuous Integration (CI)** y **Continuous Delivery (CD)**. Su objetivo general consiste en aumentar la detección temprana de errores a lo largo del ciclo de vida del desarrollo de un proyecto, optimizando cada etapa de su proceso, sin afectar la calidad del producto.

**Continuous Integration (CI)** o Integración Continua es una práctica, normalmente automatizada, que tiene como objetivo que todos los miembros de un equipo de desarrollo compartan sus cambios en la base principal del código con regularidad, comprobar su funcionamiento con el resto de elementos del proyecto tras cada cambio y asegurar que estos cambios, no afecten o generen errores al proyecto en general. En este orden de ideas, los elementos claves de CI son los siguientes:

* Un sistema de control de versiones (**git** por ejemplo) que contenga el código base del proyecto (fuentes, librerías, archivos de configuración, etc.).
* Scripts de compilación automatizados.
* Tests automatizados.
* Infraestructura en la cual ejecutar las compilaciones y las pruebas.


**Continuous Delivery (CD)** o Entrega Continua es una práctica que tiene como objetivo hacer que el proceso de lanzamiento a producción de un producto de software sea más rápido, confiable y recurrente.

Al igual que el CI, el CD se fundamenta en la automatización. Sin embargo, al final del proceso y, dependiendo del contexto de la empresa desarrolladora, el producto como tal o el cliente, puede que sea más eficiente tener un lanzamiento a producción de manera manual para: controlar la disponibilidad de nuevas funcionalidades, planificar la suspensión de los servicios del producto tras una actualización, responder a un calendario estricto, entre otros escenarios.

Paralelamente, existe el escenario de un proceso de implementación continua totalmente automatizado, normalmente nombrado dentro de la industria como **Continuous Deployment**, en donde no es necesario controlar por ninguna razón el lanzamiento a producción de las integraciones de código que realiza el equipo, por tanto, este enfoque da la posibilidad de, tras tener el código desarrollado de un determinado cambio, tenerlo en producción y funcionando en pocos minutos y desplegar varios cambios en un solo día.


### Recursos complementarios:

- [**ATLASSIAN** - Comparación de integración continua, entrega continua e implementación continua](https://www.atlassian.com/es/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment)

- [**JETBRAINS** - Guía de CI/CD de TeamCity](hhttps://www.jetbrains.com/es-es/teamcity/ci-cd-guide/)




### Ideas sueltas:

- CI/CD se construye bajo las bases de herramientas, procesos y cultura (cambio de mentalidad).

- A los conceptos de Continuous Delivery y Continuous Deplyment se suelen unir bajo el concepto de Continuous Distribution.

- En términos prácticos cuando hablamos de CI/CD hablamos de un proceso, es decir, una serie de pasos definidos para agilizar y optimizar el proceso de desarrollo de código.

- CI/CD es un workflow, son prácticas de DevOps.

- Estrategias de ramificación con enfoque CI/CD es un tema relacionado para investigar.

- Este tema obliga a tener en el radar el conocimiento de cómo evolucionaron las prácticas de desarrollo de software y los problemas que tratan de abordar Agile y DevOps puede ayudarle a sacar más provecho de su proceso de CI/CD. Un buen comienzo esta en este [link](https://www.jetbrains.com/es-es/teamcity/ci-cd-guide/devops-ci-cd/).