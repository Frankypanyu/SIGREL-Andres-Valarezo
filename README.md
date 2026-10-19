# SIGREL — Sistema Inteligente de Gestión de Reparaciones de Laptops

**Programación III · Progreso 1** | Quito, 18 de octubre de 2026

> Estado: análisis y diseño preliminar. **No existe una aplicación Java funcional todavía**.

## Autor y modalidad
**Estudiante:** Andrés Valarezo

**Modalidad:** proyecto individual de análisis y diseño.

**Responsabilidad:** Andrés Valarezo desarrolla y documenta los cinco módulos. Plan por etapas: clientes/equipos; órdenes/diagnósticos; prioridades; técnicos/asignaciones; seguimiento/pruebas.

## Problema
Un taller pequeño necesita registrar reparaciones de laptops, priorizar órdenes según urgencia y antigüedad, asignar técnicos compatibles y recuperar un historial fiable del servicio.

## Módulos propuestos
1. Clientes y equipos.
2. Órdenes y clasificación.
3. Priorización con regla de envejecimiento.
4. Técnicos y asignaciones.
5. Diagnóstico y seguimiento.

## Dos alternativas consideradas
- A: `ArrayList` + búsqueda lineal + ordenamiento de pendientes antes de consultar.
- B (seleccionada): `HashMap<Integer, OrdenReparacion>` + `PriorityQueue<OrdenReparacion>` + `ArrayList<EventoSeguimiento>`.

En B, consulta por ID: O(1) esperada; encolar y extraer: O(log p); reconstrucción del heap cuando cambia la prioridad: O(p). Las pruebas y mediciones son tareas futuras.

## Criterio de prioridad
`puntuacion = urgencia * 10 + 2 * diasDeEspera` (urgencia 1, 2 o 3). Desempate: fecha de ingreso anterior y luego menor ID. El puntaje se actualiza por lotes y se reconstruye la cola para no alterar indebidamente un `PriorityQueue`.

## Archivos de esta entrega
- `docs/entrega/Informe_SIGREL_Andres_Valarezo.pdf`: informe técnico de Progreso 1.
- `docs/entrega/Presentacion_SIGREL_Andres_Valarezo.pptx`: presentación de 10 diapositivas.
- `docs/uml/modelo_sigrel.puml` y `docs/uml/modelo_sigrel.dot`: diagrama UML editable.
- `docs/uml/UML_SIGREL.png`: vista previa del UML.

## Estructura
```text
SIGREL-Andres-Valarezo/
├── README.md
├── pom.xml
├── .gitignore
├── docs/
│   ├── entrega/Informe_SIGREL_Andres_Valarezo.pdf
│   ├── entrega/Presentacion_SIGREL_Andres_Valarezo.pptx
│   ├── fuentes/referencias.md
│   └── uml/modelo_sigrel.puml  # fuente UML editable
│   └── uml/modelo_sigrel.dot   # fuente editable alternativa
├── src/main/java/ec/edu/sigrel/  # pendiente de implementación
└── src/test/java/ec/edu/sigrel/  # pendiente de pruebas
```

## Cómo revisar UML
Abrir `docs/uml/modelo_sigrel.puml` en una herramienta UML compatible con PlantUML (por ejemplo, la extensión PlantUML del IDE), revisar clases, métodos y multiplicidades, realizar cambios y exportar la versión aprobada. El PNG compartido con el informe es una representación preliminar que requiere revisión del estudiante.

## Preparación de Progreso 2
- Implementar entidades y validación de estados.
- Construir gestor indexado y cola con comparador estable.
- Escribir casos de prueba: duplicados, prioridades, envejecimiento y asignación.
- Integrar y documentar decisiones y mediciones de rendimiento.

## Repositorio GitHub
Repositorio creado: https://github.com/Frankypanyu/SIGREL-Andres-Valarezo

Para completar la publicación, subir el contenido de esta carpeta mediante **Upload files** y confirmar los cambios con **Commit changes**. El contenido del ZIP no se publica automáticamente.

## Fuentes
Ver `docs/fuentes/referencias.md` y el informe PDF.

## IA utilizada
ChatGPT ayudó a preparar este borrador y la estructura preliminar. Todos los elementos requieren verificación académica y técnica por el estudiante antes de la entrega.
