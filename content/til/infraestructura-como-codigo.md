---
author: 'Alejo Henao'
title: 'Qué es la Infraestructura como Código -IaC-'
date: '2021-01-20'
description: 'Definición rápida de la Infraestructura como Código y sus ventajas en el desarrollo de sofware'
tags: ['IaC']
categories: ['Conceptos']
series: ['DevOps']
aliases: ['infraestructura-como-codigo']
ShowToc: false
TocOpen: false
hideSummary: false

---

**La infraestructura como código -IaC- (Infrastructure as Code)**, es una práctica de DevOps que permite a los desarrolladores administrar y aprovisionar la infraestructura de un proyecto (programar estructuras de hardware) a través de código en lugar de realizar configuraciones a través de procesos manuales.

Ahora bien, *¿por qué hoy día la IaC es tan relevante en la industria?* la respuesta a esta pregunta pasa por el nivel de complejidad que hoy día caracteriza a los productos de software.

Ahora mismo, es muy difícil planificar y ejecutar un proyecto soportado en un único servidor en el cual aprovisionar todas los requerimientos para el proyecto. Hoy, las necesidades de los proyectos de software implican tener una infraestructura distribuída en varias máquinas, escalar servicios de forma rápida, replicar ambientes para hacer testing sin dañar los ambientes de producción, etc. Crear manualmente cada elemento de nuestra infraestructura a niveles medios y altos de complejidad,es difícil de replicar, genera una mayor probabilidad de errores.

Con la IaC, los equipos pueden hacer cambios en los entornos en un archivo de configuración que normalmente tiene formato JSON, YAML o similar. Al ser código, tiene la facultad de poder integrar un sistema de control de versiones y así cuando se registra un cambio, normalmente hay un sistema de integración que genera los entornos como se indica en el archivo del modelo. Al igual que un mismo código fuente genera siempre el mismo binario, un modelo de infraestructura como código genera siempre el mismo entorno cada vez que es desplegada.

### Recursos complementarios:

- [**RedHat** - ¿Qué es la infraestructura como código (IaC)?](https://www.redhat.com/es/topics/automation/what-is-infrastructure-as-code-iac)
- [**ComputerWeekly** - Infrastructure-as-Code series - Ondat: IaC is the means to a DevOps end](https://www.computerweekly.com/blog/CW-Developer-Network/Infrastructure-as-Code-series-Ondat-IaC-is-the-means-to-a-DevOps-end)
- [**Documento académico** - DevOps: un vistazo rápido](https://repository.uaeh.edu.mx/revistas/index.php/huejutla/article/view/8121)

### Ideas sueltas:

- Con IaC es clave en las prácticas de DevOps y se usa en conjunto en Continuous Deployment.

- Con IaC los cambios siempre se hacen en el modelo, nunca en los entornos.

- La IaC facilita que diferentes equipos puedan trabajar juntos, estableciendo una serie de prácticas y herramientas comunes.

- Implementar una política de IaC en un proyecto o empresa debería de poner en el centro de su desarrollo la colaboración como motor y eje articulador.
