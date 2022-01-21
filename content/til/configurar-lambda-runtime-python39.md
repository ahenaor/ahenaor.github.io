---
author: 'Alejo Henao'
title: 'Cómo configurar una función Lambda para ejecutarse con Runtime Python 3.9 con pandas'
date: '2021-01-19'
description: 'Este artículo muestra de manera concreta una propuesta de paso a paso para configurar una función Lambda bajo un Runtime Python 3.9 con arquitectura x86_64.'
tags: ['Lambda', 'Python', 'pandas']
categories: ['AWS']
series: ['Notas Prácticas']
aliases: ['configurar-lambda-runtime-python39-pandas']
ShowToc: false
TocOpen: false
---

**AWS Lambda** es un servicio que permite ejecutar código sin preocuparnos por la infraestructura de los servidores donde corren -Serverless-. Esto lo convierte en un servicio muy potente y práctico para implementar una gran variedad de proyectos.

**AWS Lambda** es compatible de forma nativa con Java, Go, PowerShell, Node.js, C#, [Python](https://docs.aws.amazon.com/lambda/latest/dg/python-package.html) y Ruby.

**AWS Lambda** incluye los módulos integrados en la versión de Python que despliegues (2.7, 3.6, 3.7, 3.8 o 3.9) como por ejemplo json. Adicionalmente, incluye **boto3** ya que es la librería oficial de AWS para las integraciones de nuestras aplicaciones en Python con los servicios de AWS como **S3, EC2, DynamoDB** entre otros.


### Tiempos de ejecución de Python

| Nombre    | AWS SDK                          | Sistema Operativo | Arquitecturas |
|-----------|----------------------------------|-------------------|---------------|
| python3.9 | boto3-1.18.55 botocore-1.21.55   | Amazon Linux 2    | x86_64, arm64 |
| python3.8 | boto3-1.18.55 botocore-1.21.55   | Amazon Linux 2    | x86_64, arm64 |
| python3.7 | boto3-1.18.55 botocore-1.21.55   | Amazon Linux      | x86_64        |
| python3.6 | boto3-1.18.55 botocore-1.21.55   | Amazon Linux      | x86_64        |
| python2.7 | boto3-1.17.100 botocore-1.20.100 | Amazon Linux      | x86_64        |

**Fuente:** [AWS](https://docs.aws.amazon.com/es_es/lambda/latest/dg/lambda-runtimes.html)

Evidentemente, en la gran mayoría de los casos de uso de funciones Lambda con Python, vamos a requerir utilizar librerías externas que nos ayuden a codificar la lógica de nuestra función. 

#### En este ejemplo práctico, vamos a aprovisionar una función Lambda para ejecutarse con Python 3.9 incluyendo la librería pandas.

Lo primero que debemos hacer es crear la función Lambda a través de la interfaz de consola de AWS:

- Seleccione la opción de “Comience con un ejemplo simple de Hello World”.
- Escriba un nombre apropiado para su función Lambda.
- Seleccione el runtime Python 3.9.
- Seleccione la arquitectura x86_64. 
- En permisos seleccione la opción “Cree un nuevo rol con permisos básicos de Lambda”.
- Clic en el botón Create functions.

**Luego, debemos preparar una [capa de Python](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html) con librería Pandas:**

La librería pandas es un potente kit de herramientas de análisis de datos de Python. Cuando se instala pandas, de manera automática el sistema instala otras dependencias de pandas como lo son pytz, python-dateutil y numpy.

Con Numpy pasa un caso particular y es que su compilación deber ser exactamente igual a la máquina en la que se va a ejecutar. Si revisamos el cuadro donde vemos las características de cada runtime de Python vemos que la versión 3.9 se va a ejecutar en Lambda en un sistema operativo Amazon Linux 2. Por tanto es necesario que numpy sea compilado en una máquina igual.

Para resolver esto, lo que vamos a hacer es:

1. Crear una instancia de EC2 con Amazon Linux 2.
2. En la EC2 Instalar Python 3.9 - Podemos seguir esta [guía](https://techviewleo.com/how-to-install-python-on-amazon-linux-2/)
3. Instalar virtualenv
    
    `pip3.9 install virtualenv`
4. Crear un directorio, por ejemplo: **compilacion-pandas** y allí crear un entorno virtual.

    `virtualenv venv`

    `source venv/bin/activate`

5.  Instalar pandas

    `pip3.9 install pandas`

6. Copiar lib o lib64 a un directorio llamado python.

    `cp -r /home/ec2-user/pandas/venv/lib64 /home/ec2-user/pandas/venv/python`

7. Renombrar lib64 a lib

    `mv lib64 lib`

8. Ir a la raiz de la instancia e instalar AWS CLI

    `curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install`

9. Eliminar basura, comprimir en .zip la carpeta python y enviarla a S3

    `rm -r *.whl *.dist-info __pycache__`

    `zip -r9 pandas39.zip python`

    `aws s3 cp pandas39.zip s3://bucket-0574-base`

En este punto ya tenemos en S3 nuestro .zip con pandas compilado en una máquina Amazon Linux 2.

Ahora lo úlitmo que debemos hacer es ir ala función Lambda y en el apartado Layers crear un nuevo Layer compatible con el rumtime Python 3.9 y la arquitectura x86_64 y finalmente cargamos el .zip desde S3.

### Recursos complementarios:
- [**AWS** - How do I resolve the "Unable to import module" error that I receive when I run Lambda code in Python?](https://aws.amazon.com/premiumsupport/knowledge-center/lambda-import-module-error-python/)
- [**AWS** - Creating and sharing Lambda layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html)
- [**AWS** - Building Lambda functions with Python](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html)
- [**AWS** - Installing or updating the latest version of the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- [**Medium** - AWS Lambda with Pandas and NumPy](https://korniichuk.medium.com/lambda-with-pandas-fd81aa2ff25e)
- [**TechView** - How To Install Python 3.10 on Amazon Linux 2 ](https://techviewleo.com/how-to-install-python-on-amazon-linux-2/)
- [**gitconnected** - Implementación en AWS Lambda: Python + Layers + CloudWatc](https://levelup.gitconnected.com/deploying-to-aws-lambda-python-layers-cloudwatch-31c4119d3a69)


### Ideas sueltas:
- Es fundamental aprender a realizar esta misma configuración pero desde el enfoque de infraestructura como código.
