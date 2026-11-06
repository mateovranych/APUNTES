# APUNTES

Colección de apuntes de **Ingeniería / Programación** pensados para estudiar, repasar antes de un parcial y tener a mano como referencia rápida. Todos comparten el mismo diseño en blanco y negro, están escritos en español y combinan **teoría + código real** (C# / .NET en el backend, Angular/TypeScript en el frontend).

Cada apunte está pensado como una unidad autocontenida: arranca desde el "¿por qué?", explica el concepto, muestra el código paso a paso y cierra con un resumen comparativo, errores comunes y glosario.

---

## Índice

| # | Apunte | Tema central | Stack |
|---|--------|--------------|-------|
| 1 | [APUNTE_APIS.pdf](#1-apunte_apispdf--apis-rest-con-net) | Construir una API REST de cero | .NET / C# / EF Core |
| 2 | [APUNTE_ANGULAR_2.pdf](#2-apunte_angular_2pdf--angular--autenticación) | Autenticación en el frontend | Angular / JWT |
| 3 | [APUNTE_ANGULAR_ROLES.pdf](#3-apunte_angular_rolespdf--autorización-por-roles) | Autorización por roles | Angular + .NET / JWT |
| 4 | [APUNTE_PAGINACION_FILTRADO.pdf](#4-apunte_paginacion_filtradopdf--paginación-y-filtrado) | Paginar y filtrar listados | .NET + Angular |
| 5 | [APUNTE_TESTING.pdf](#5-apunte_testingpdf--testing-y-tdd) | Testear software | xUnit / Moq |
| 6 | [APUNTE_CODESMELLS.pdf](#6-apunte_codesmellspdf--code-smells-y-refactoring) | Detectar y arreglar malos olores | Refactoring |
| 7 | [Apunte_Clean_Architecture.pdf](#7-apunte_clean_architecturepdf--clean-architecture) | Organizar el proyecto en capas | Arquitectura / .NET |
| 8 | [APUNTE_UML.pdf](#8-apunte_umlpdf--uml-y-modelado) | Modelar antes de programar | UML |
| 9 | [Apunte de ingenieria.pdf](#9-apunte-de-ingenieriapdf--ingeniería-de-software) | Panorama completo de la materia | Teoría integral |
| 10 | [Apunte_Redes_Ciberseguridad.pdf](#10-apunte_redes_ciberseguridadpdf--redes-y-ciberseguridad) | Cómo funcionan las redes y los ataques | Redes / Seguridad |

---

## 1. `APUNTE_APIS.pdf` — APIs REST con .NET

**Qué ataca:** la pregunta de "¿cómo construyo una API de verdad?". Es el apunte base del backend: te lleva desde cómo viaja un dato por internet hasta tener una API en .NET funcionando con base de datos.

**Qué explica:**
- **HTTP y la web:** protocolo HTTP/HTTPS, verbos (GET, POST, PUT, DELETE, PATCH), códigos de estado (2xx, 4xx, 5xx) y headers.
- **REST, SOAP, endpoints y JSON:** qué es REST y en qué se diferencia de SOAP, qué es un endpoint y cómo se estructura el JSON.
- **Autenticación con JWT:** el flujo de login → token → request protegido, y cómo proteger endpoints en .NET.
- **C# esencial:** funciones lambda, variables, clases, clases estáticas e interfaces.
- **Arquitectura de una API .NET:** servicios, controladores, `Program.cs`, inyección de dependencias (DI) e `IActionResult`.
- **Persistencia con Entity Framework Core:** qué es un ORM, el `DbContext`, migraciones, consultas con LINQ y los métodos más usados de EF.
- **Validación, errores, middleware y CORS:** Data Annotations, manejo de errores, qué es un middleware y por qué hace falta CORS.
- **Asincronía y el CLR:** `async`/`await` y qué es el Common Language Runtime.
- Cierra con el **flujo completo de un request**, ejercicios en tres niveles y un glosario.

---

## 2. `APUNTE_ANGULAR_2.pdf` — Angular + Autenticación

**Qué ataca:** el lado del cliente del login. Una vez que la API devuelve un token, ¿cómo lo maneja el frontend? Este apunte conecta Angular con el backend .NET.

**Qué explica:**
- **Flujo de autenticación completo:** el circuito de punta a punta entre frontend y backend.
- **AuthService:** el modelo de login y respuesta, el servicio completo y el componente de Login.
- **Interceptors (el middleware de Angular):** qué son, el interceptor de autenticación que agrega el JWT a cada request, el interceptor de errores HTTP y cómo registrarlos.
- **Guards:** qué son y cómo proteger rutas para que un usuario no autenticado no entre.
- **Pipes:** qué son, los pipes incorporados, cómo usarlos y cómo crear uno personalizado.
- Cierra con el **flujo completo** (todo junto) y un cuadro comparativo backend vs frontend.

---

## 3. `APUNTE_ANGULAR_ROLES.pdf` — Autorización por roles

**Qué ataca:** la diferencia entre *autenticación* (quién sos) y *autorización* (qué podés hacer). Resuelve cómo hacer que un admin vea cosas que un usuario común no.

**Qué explica:**
- **Por qué autorización por roles** y la anatomía del **JWT**: sus tres partes, qué son los claims, cómo se genera el token en .NET, qué significa `Bearer` y el ciclo de vida completo del token.
- **Backend:** agregar la propiedad `Rol` a la entidad Usuario, generar la migración, incluir el rol como claim y proteger endpoints por rol.
- **Frontend:** decodificar el payload del JWT en Angular, nuevos métodos en el `AuthService`, un **guard de roles**, mostrar/ocultar elementos según el rol con `*ngIf`, un navbar dinámico y un componente "Sin Permiso".
- Cierra con dos escenarios (admin accede / usuario común es rechazado) y resumen.

---

## 4. `APUNTE_PAGINACION_FILTRADO.pdf` — Paginación y filtrado

**Qué ataca:** el problema de traer 10.000 registros de golpe. Enseña a partir los listados en páginas y a filtrarlos, tanto en el backend como en el frontend.

**Qué explica:**
- **Por qué paginar** y los **query parameters** como mecanismo de comunicación.
- **Backend (.NET + LINQ):** el DTO de respuesta paginada, el servicio con paginación y filtrado (`Skip`/`Take`) y el controlador.
- **Frontend (Angular):** el modelo e interfaz, el servicio con `HttpParams`, el componente y el template HTML.
- **Filtrado avanzado:** múltiples filtros combinados en backend y frontend.
- **Debounce:** optimizar la búsqueda en tiempo real para no disparar una request por cada tecla.
- Cierra con flujo completo, comparativo y errores comunes.

---

## 5. `APUNTE_TESTING.pdf` — Testing y TDD

**Qué ataca:** la confianza en el código. ¿Cómo sé que lo que programé funciona y que no lo rompí al cambiar algo?

**Qué explica:**
- **Qué es el testing:** por qué testear, verificación vs validación y tipos de errores.
- **Pirámide de pruebas:** unitarias, de integración y E2E.
- **Patrón AAA** (Arrange-Act-Assert) con ejemplo completo en C#.
- **xUnit:** configuración, `[Fact]` vs `[Theory]`, `[InlineData]` y los asserts más usados.
- **Mocks, Stubs y Fakes:** diferencias, un stub manual y un mock con **Moq**.
- **Cobertura de código:** cómo medirla con `dotnet` y qué conviene testear y qué no.
- **TDD:** el ciclo Red-Green-Refactor con un ejemplo paso a paso.
- Cierra con buenas prácticas, errores comunes y glosario.

---

## 6. `APUNTE_CODESMELLS.pdf` — Code smells y refactoring

**Qué ataca:** el código que "funciona pero huele mal". Enseña a reconocer síntomas de mal diseño y a arreglarlos sin romper nada.

**Qué explica:**
- **Qué es un code smell** y la diferencia entre smell, bug y deuda técnica.
- Las **cinco familias de smells**:
  - **Bloaters** (código que creció de más): método largo, clase dios, obsesión por primitivos, data clumps.
  - **Abusadores de la OO:** switch repetido, herencia rechazada, campo temporal.
  - **Smells que frenan el cambio:** cirugía de escopeta.
  - **Prescindibles:** código duplicado, comentarios tapadera, código muerto, generalidad especulativa.
  - **Acopladores:** feature envy, cadenas de mensajes, intimidad inapropiada, intermediario inútil.
- **Cómo detectarlos y refactorizar seguro:** tabla resumen, valores orientativos y técnica de refactoring seguro.
- Cierra con un **ejercicio integrador** con solución y glosario.

---

## 7. `Apunte_Clean_Architecture.pdf` — Clean Architecture

**Qué ataca:** el caos de un proyecto donde todo depende de todo. Enseña a organizar el código en capas para que sea mantenible y testeable.

**Qué explica:**
- **Qué es Clean Architecture** y la **regla de dependencia** (las dependencias apuntan hacia adentro).
- **Las capas y sus responsabilidades:** Domain (entidades), Application (casos de uso), Infrastructure y Presentation/API, con su estructura de carpetas.
- **Puertos y adaptadores:** qué son y los tipos de puertos.
- **Refactoring guiado:** de una estructura plana (ANTES) a Clean Architecture (DESPUÉS), paso a paso.
- **Dónde encajan los patrones de diseño** (ej. Decorator para caché).
- **Testing por capa:** qué se testea en cada una y por qué sin Clean Architecture es más difícil.
- **Del commit al deploy:** estructura en el `Dockerfile` y pipeline de GitHub Actions (CI/CD).
- Cierra con resumen y glosario del bloque.

---

## 8. `APUNTE_UML.pdf` — UML y modelado

**Qué ataca:** pensar y comunicar el diseño *antes* de escribir una línea de código. Es el apunte de los diagramas que caen en los parciales.

**Qué explica:**
- **Qué es UML** y para qué sirve modelar, con los tipos de diagramas.
- **Diagrama de clases:** atributos, métodos, relaciones entre clases y multiplicidad (cardinalidad).
- **Diagrama de casos de uso:** elementos e `include` vs `extend`.
- **Diagrama de secuencia:** elementos y ejemplo de flujo.
- **Diagrama de estados** y **diagrama de actividad**, con ejemplos.
- Cierra con "¿qué diagrama uso?", errores comunes en parciales y glosario.

> Los ejemplos están ambientados en una lomitería (pedidos, choripán, lomito completo) para que los conceptos entren fácil.

---

## 9. `Apunte de ingenieria.pdf` — Ingeniería de Software

**Qué ataca:** el panorama completo de la materia. Es el apunte "paraguas" que conecta todos los demás y sirve para el parcial teórico.

**Qué explica:**
- **Software y hardware:** qué es cada uno, tipos de software y qué es la ingeniería de software.
- **Ciclo de vida (SDLC):** las 7 fases, modelos de proceso (cascada, iterativo/incremental, espiral) y requerimientos funcionales vs no funcionales.
- **Calidad de software:** atributos ISO 25010, deuda técnica, cohesión y acoplamiento.
- **Patrones de diseño:** creacionales (Singleton, Factory, Builder), estructurales (Adapter, Decorator, Facade) y de comportamiento (Observer, Strategy, Repository, Command).
- **Principios SOLID** (uno por uno).
- **Arquitecturas:** monolito, microservicios y cuándo usar cada uno.
- **Metodologías ágiles:** Manifiesto Ágil, Scrum, Kanban y su comparación.
- **Conceptos complementarios:** Git, pirámide de testing, DevOps y CI/CD, principios DRY/KISS/YAGNI, UML y tipos de pruebas.
- Cierra con un glosario rápido.

---

## 10. `Apunte_Redes_Ciberseguridad.pdf` — Redes y Ciberseguridad

**Qué ataca:** cómo viajan los datos por una red y cómo se piensan los ataques. Mezcla fundamentos de redes con una introducción práctica a la ciberseguridad ofensiva.

**Qué explica:**
- **Modelo OSI** y encapsulación.
- **Capa 3 (IP y subredes):** rangos de IPs privadas y la máscara de subred.
- **Capa 2 (MAC y ARP)** con comandos útiles.
- **Capa 4 (TCP y UDP)** y su relevancia para un **port scanner**.
- **Puertos y servicios** más comunes.
- **DNS:** tipos de registros y comandos de exploración.
- **HTTP:** métodos y códigos de estado.
- **Firewalls y NAT.**
- **Reverse shell:** por qué funciona.
- **Kill Chain:** las etapas del ciclo de un ataque.
- **Subnetting:** cálculo rápido para partir redes a medida.

---

## Cómo usar estos apuntes

- Son **PDFs** listos para leer en cualquier dispositivo, imprimir o anotar.
- Se pueden estudiar sueltos, pero tienen un orden sugerido: empezá por **Ingeniería** (panorama), seguí con **APIs → Angular → Roles → Paginación** (el camino full-stack), y usá **Testing, Code Smells, Clean Architecture y UML** como apuntes de buenas prácticas. **Redes y Ciberseguridad** es una unidad aparte.

---

*Apuntes de uso personal/educativo. Si te sirven, usalos libremente.*
