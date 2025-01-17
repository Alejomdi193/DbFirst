# Proyecto DB First con .NET

Este proyecto consiste en la generación de un modelo de datos en un proyecto de C# (.NET) a partir de una base de datos existente en MySQL utilizando el enfoque **Database First (DB First)**.

## Tecnologías Utilizadas

- **.NET**: Framework para desarrollar aplicaciones.
- **MySQL**: Sistema de gestión de bases de datos relacional utilizado como fuente de datos.
- **Entity Framework Core**: Herramienta ORM (Mapeo Objeto-Relacional) para interactuar con la base de datos de forma eficiente.

## Requisitos Previos

1. Tener instalado:
   - .NET SDK.
   - MySQL Server.
   - Herramientas de desarrollo como Visual Studio o Visual Studio Code.
2. Contar con una base de datos MySQL configurada y accesible.
3. Instalar el paquete de herramientas de Entity Framework Core compatible con MySQL. Ejemplo:
   ```bash
   dotnet add package Pomelo.EntityFrameworkCore.MySql
   ```

## Pasos Realizados

### 1. Conexión a la Base de Datos

Se configuró una cadena de conexión en el archivo `appsettings.json` para conectarse a la base de datos MySQL:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=NombreDeTuBaseDeDatos;User=root;Password=tuContraseña;"
  }
}
```

### 2. Instalación de Paquetes Necesarios

Se añadieron los siguientes paquetes al proyecto:

- `Microsoft.EntityFrameworkCore`
- `Microsoft.EntityFrameworkCore.Tools`
- `Pomelo.EntityFrameworkCore.MySql`

### 3. Generación de los Modelos DB First

Se ejecutó el siguiente comando para generar los modelos y el contexto de la base de datos:

```bash
dotnet ef dbcontext scaffold "server=localhost;user=root;password=123456789;database=jardineriadb" Pomelo.EntityFrameworkCore.MySql --context ProduccionContext --context-dir Data --output-dir Entities
```

Este comando generó las clases de modelo correspondientes a las tablas de la base de datos y una clase `ProduccionContext` para administrar la interacción con la base de datos.

### 4. Organización del Proyecto

El proyecto se organizó en carpetas para mantener una estructura clara:

- **Entities**: Contiene los modelos generados por Entity Framework Core.
- **Data**: Incluye configuraciones adicionales de `ProduccionContext` si es necesario.
- **Controllers**: Contiene la lógica de negocio para interactuar con los modelos y la base de datos.
- **Views**: (Si aplica) Maneja la interfaz de usuario para mostrar los datos.

### 5. Pruebas

Se realizaron pruebas para verificar que la conexión a la base de datos y las operaciones CRUD (Crear, Leer, Actualizar, Eliminar) funcionaran correctamente utilizando los modelos generados.

## Cómo Ejecutar el Proyecto

1. Clona el repositorio.

2. Configura tu cadena de conexión en el archivo `appsettings.json`.

3. Restaura los paquetes necesarios ejecutando:

   ```bash
   dotnet restore
   ```

4. Inicia el proyecto:

   ```bash
   dotnet run
   ```

