# Bicis Damián - Hugo, René y Franco


Proyecto de despliegue de una infraestructura de gestión utilizando Docker Compose, con Odoo como aplicación principal, PostgreSQL como sistema de gestión de bases de datos y pgAdmin para su administración.


## Tecnologías utilizadas


- **Odoo 18.0:** aplicación de gestión empresarial.
- **PostgreSQL 15.10:** base de datos relacional.
- **pgAdmin 4 (9.1.0):** administración gráfica de PostgreSQL.
- **Docker:** ejecución de los servicios mediante contenedores.
- **Docker Compose:** configuración y coordinación de los servicios.


## Arquitectura


El proyecto está compuesto por tres servicios:


| Servicio | Puerto | Función |
|---|---:|---|
| Odoo | 8069 | Aplicación web |
| PostgreSQL | 5432 | Base de datos |
| pgAdmin | 5050 | Administración de la base de datos |


Los servicios se comunican mediante la red interna de Docker Compose. PostgreSQL utiliza un volumen persistente para conservar los datos.


## Estructura del proyecto


```text
bicis-damian/
├── compose.yaml
├── .env.example
├── README.md
└── evidencias/
   └── md.md
```


- `compose.yaml`: definición de los servicios, puertos, variables de entorno, volúmenes y dependencias.
- `.env.example`: plantilla de las variables de entorno necesarias.
- `README.md`: documentación del proyecto.
- `evidencias/`: documentación y capturas del proceso de instalación y las pruebas realizadas.


## Requisitos


- Ubuntu 22.04 LTS.
- Docker Engine.
- Docker Compose.
- Conexión a Internet para descargar las imágenes.


## Instalación y ejecución


### 1. Configurar las variables de entorno


Crear el archivo `.env` a partir de la plantilla:


```bash
cp .env.example .env
```


Editar `.env` y establecer las contraseñas necesarias para PostgreSQL, Odoo y pgAdmin. No publicar este archivo en GitHub.


### 2. Validar la configuración


```bash
sudo docker compose config
```


### 3. Descargar las imágenes


```bash
sudo docker compose pull
```


### 4. Iniciar los servicios


```bash
sudo docker compose up -d
```


### 5. Comprobar el estado


```bash
sudo docker compose ps
```


Los servicios deben aparecer en ejecución y el contenedor de PostgreSQL debe superar su comprobación de salud.


### 6. Acceder a las aplicaciones


- Odoo: http://localhost:8069
- pgAdmin: http://localhost:5050


Las credenciales se configuran localmente mediante el archivo `.env`.


## Persistencia de datos


Se han configurado volúmenes de Docker para PostgreSQL, Odoo y pgAdmin. Esto permite conservar los datos y la configuración almacenados en dichos volúmenes al detener o reiniciar los contenedores.


La persistencia se comprobó creando un contacto de prueba en Odoo y verificando que seguía disponible después de reiniciar los servicios.


--Hugo
