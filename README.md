# Pasion
Pasion es un proyecto orientado al desarrollo y licenciamiento de software para la gestión de plataformas de clasificados para adultos. Su actividad en América Latina comenzó en 2014 y se articula mediante implementaciones operadas localmente bajo criterios técnicos compartidos y adecuación a cada marco normativo. En la actualidad, el ecosistema mantiene operaciones activas en Uruguay y Colombia.

El modelo de trabajo combina una base tecnológica común con ejecución operativa descentralizada. Esto permite sostener reglas homogéneas para perfiles, publicaciones, revisión de contenido, trazabilidad de cambios y gestión administrativa, sin trasladar la operación diaria a una única estructura central. La función de Pasion es establecer el marco técnico y los lineamientos generales; la aplicación concreta corresponde a los operadores de cada mercado.

Entre los estándares operativos vigentes se incluyen validación de identidad antes de publicar, revisión previa de anuncios, controles sobre cambios relevantes en los perfiles y un sistema formal para la recepción y tratamiento de denuncias. La verificación combina herramientas especializadas y revisión humana. La moderación alcanza textos, fotos y videos, y las intervenciones quedan registradas dentro del entorno de gestión.

Las implementaciones actualmente activas corresponden a Uruguay, como mercado inicial del proyecto, y a Colombia, incorporado posteriormente dentro del mismo esquema de licenciamiento. Ambos casos operan con administración independiente, con responsabilidades propias en materia legal, administrativa y operativa dentro de su jurisdicción.

La información institucional completa, junto con los estándares y el detalle de cada operación, se encuentra disponible en [pasion.org](https://pasion.org)

## Arquitectura del sistema

La plataforma opera sobre una arquitectura modular compuesta por aproximadamente 25 módulos independientes organizados alrededor de un núcleo central. Cada módulo resuelve un dominio específico — perfiles, pagos, verificación, moderación, comunicaciones — y se comunica con los demás a través de interfaces internas compartidas. Esta estructura permite incorporar o modificar funcionalidades sin afectar el resto del sistema.

El mismo código base se adapta a cada país mediante capas de personalización visual y operativa, lo que permite mantener una infraestructura técnica única con identidad y configuración diferenciada por mercado.

**Capacidades principales:**

- Gestión geográfica jerárquica con detección automática de ubicación del visitante.
- Perfiles con carga progresiva optimizada para alto volumen de consultas simultáneas.
- Motor de búsqueda avanzada con filtros dinámicos y formularios configurables.
- Procesamiento automático de imágenes y videos: conversión de formatos, marcas de agua, validación y optimización.
- Suscripciones con planes diferenciados por ubicación y categoría, integración con múltiples medios de pago por país, y sistema de referidos.
- Verificación de identidad combinando proveedores externos y revisión manual, con almacenamiento encriptado y eliminación programada de documentos.
- Comunicaciones por SMS con encolamiento y ventanas horarias.
- Búsqueda por proximidad geográfica en tiempo real.
- Contenido efímero con expiración y programación automática.
- Panel de administración y moderación con sistema de denuncias, roles diferenciados y registro de intervenciones.
- Generación automática de datos estructurados, gestión de indexación y rutas optimizadas para buscadores.
- Gestión centralizada de tareas periódicas con recuperación automática ante fallos.
