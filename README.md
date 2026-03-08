# Zoo

Proyecto Java EE para gestión de un zoológico, estructurado en capas (`entities`, `persistence`, `logic` y `dto`) y empaquetado como `WAR` para despliegue en un servidor compatible con Java EE 7.

## 🧩 Tecnologías principales

- **Java EE 7** (`javax:javaee-web-api:7.0`)
- **JPA 2.x** (`javax.persistence-api` + EclipseLink)
- **EJB Stateless** en las capas de lógica y persistencia
- **Maven** para construcción y dependencias
- **Empaquetado `war`** para despliegue en servidor de aplicaciones

## 📁 Estructura del proyecto

```text
src/main/java/co/edu/konrad/zoo/
├── dto/          # Objetos de transferencia de datos
├── entities/     # Entidades JPA del dominio
├── logic/        # Reglas de negocio
└── persistence/  # Acceso a datos (EntityManager)

src/main/resources/META-INF/persistence.xml
src/main/webapp/WEB-INF/glassfish-resources.xml
```

## 🐾 Dominio modelado

El proyecto incluye entidades para administrar la operación de un zoológico, por ejemplo:

- Animales, especies y tipos de animal/alimento
- Cuidadores y personas
- Horarios y planificación de alimentación
- Shows y relación animal-show
- Lugares y calificaciones

## ⚙️ Configuración de base de datos

El proyecto está configurado para usar un datasource JTA con nombre **`java:app/ZooDB`** y creación automática de esquema (`create`) desde JPA.

### Configuración incluida para GlassFish

En `glassfish-resources.xml` se define:

- Pool JDBC `derby_net_sample_appPool`
- Driver Derby cliente (`org.apache.derby.jdbc.ClientDriver`)
- URL: `jdbc:derby://localhost:1527/sample`
- Recurso JNDI: `java:app/ZooDB`

> Si usas otro motor o credenciales distintas, ajusta este archivo y `persistence.xml` según tu entorno.

## ▶️ Cómo compilar

```bash
mvn clean package
```

Esto generará el archivo `WAR` en `target/`.

## 🚀 Despliegue (referencia)

1. Inicia tu servidor Java EE (por ejemplo GlassFish/Payara).
2. Asegúrate de crear/configurar el datasource `java:app/ZooDB`.
3. Despliega el `WAR` generado en `target/`.
4. Verifica la aplicación en el contexto que asigne el servidor.

## 🧪 Pruebas

Para ejecutar pruebas unitarias:

```bash
mvn test
```

> Nota: en este entorno, la resolución de plugins Maven puede depender del acceso al repositorio remoto configurado.

## 📌 Estado actual

Actualmente la página `index.html` es una vista base (`Hello World`) y el foco del proyecto está en la estructura backend de dominio, lógica y persistencia.

---

Si quieres, en un siguiente paso puedo agregarte también:

- Diagrama de capas del proyecto
- Guía de endpoints (si vas a exponer API REST)
- Script SQL inicial para poblar datos de prueba
