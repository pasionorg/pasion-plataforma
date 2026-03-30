# Pasion
Pasion es un proyecto orientado al desarrollo y licenciamiento de software para la gestión de plataformas de clasificados para adultos. Su actividad en América Latina comenzó en 2014 y se articula mediante implementaciones operadas localmente bajo criterios técnicos compartidos y adecuación a cada marco normativo. En la actualidad, el ecosistema mantiene operaciones activas en Uruguay y Colombia.

El modelo de trabajo combina una base tecnológica común con ejecución operativa descentralizada. Esto permite sostener reglas homogéneas para perfiles, publicaciones, revisión de contenido, trazabilidad de cambios y gestión administrativa, sin trasladar la operación diaria a una única estructura central. La función de Pasion es establecer el marco técnico y los lineamientos generales; la aplicación concreta corresponde a los operadores de cada mercado.

Entre los estándares operativos vigentes se incluyen validación de identidad antes de publicar, revisión previa de anuncios, controles sobre cambios relevantes en los perfiles y un sistema formal para la recepción y tratamiento de denuncias. La verificación combina herramientas especializadas y revisión humana. La moderación alcanza textos, fotos y videos, y las intervenciones quedan registradas dentro del entorno de gestión.

Las implementaciones actualmente activas corresponden a Uruguay, como mercado inicial del proyecto, y a Colombia, incorporado posteriormente dentro del mismo esquema de licenciamiento. Ambos casos operan con administración independiente, con responsabilidades propias en materia legal, administrativa y operativa dentro de su jurisdicción.

La información institucional completa, junto con los estándares y el detalle de cada operación, se encuentra disponible en [pasion.org](https://pasion.org)

## Descripción Técnica General del Sistema

Pasion es una plataforma web construida sobre WordPress como base, extendida mediante una arquitectura modular de plugins propietarios interconectados.

Arquitectura general. El ecosistema se compone de aproximadamente 25 plugins independientes que se comunican entre sí a través de funciones compartidas, hooks de WordPress y tablas de base de datos propias. Existe un plugin central (core) del cual dependen todos los demás, que provee funcionalidades transversales como encriptación de datos sensibles, sistema de notificaciones internas, gestión de páginas y restricciones de acceso por rol. Sobre este núcleo, cada plugin resuelve un dominio específico del negocio.

Gestión geográfica. El sistema opera con una estructura jerárquica de países, ciudades y barrios, cada uno con coordenadas geográficas. Un mecanismo de detección automática identifica la ubicación del visitante combinando cookies, parámetros de URL y headers del servidor, lo que permite personalizar la experiencia sin intervención del usuario.

Perfiles y contenido. Los perfiles se modelan como Custom Post Types de WordPress, lo que permite aprovechar de forma nativa las taxonomías, metadatos y sistema de búsqueda del CMS. El sistema incluye carga infinita optimizada con precarga de metadatos en lote (una sola consulta para múltiples perfiles), reduciendo significativamente las consultas a base de datos.

Búsqueda y filtrado. Existe un motor de búsqueda avanzada configurable que genera formularios dinámicos y traduce las selecciones del usuario a consultas optimizadas usando taxonomías y meta queries. Los formularios se cargan por AJAX para evitar problemas con cachés de página.

Multimedia. El sistema procesa y normaliza automáticamente imágenes y videos subidos por los usuarios: convierte formatos no estándar, aplica marcas de agua configurables, valida tipos MIME y optimiza resoluciones. La carga es asíncrona con previsualización en tiempo real.

Suscripciones y pagos. La plataforma opera con un modelo de suscripción por planes con diferentes niveles, duraciones y precios que pueden variar según la ciudad y categoría. Se integra con múltiples pasarelas de pago según el país de operación. Incluye un sistema de referidos con comisiones escalonadas y balance por perfil.

Verificación de identidad (KYC). Los perfiles pasan por un proceso de verificación de identidad que puede ser manual o mediante un proveedor externo. Los datos sensibles se almacenan encriptados y las fotografías de documentos se eliminan automáticamente después de un período definido.

Comunicaciones. El sistema cuenta con envío de SMS a través de una cola en base de datos, procesada por tareas programadas dentro de ventanas horarias específicas. Los mensajes se normalizan para compatibilidad con redes GSM.

Geolocalización. Una funcionalidad de proximidad calcula distancias en tiempo real usando la fórmula de Haversine, permitiendo a los visitantes encontrar perfiles cercanos a su ubicación con un radio configurable.

Contenido efímero. Similar a las "historias" de redes sociales, el sistema permite publicar contenido temporal con expiración automática. Incluye un módulo de programación que permite automatizar publicaciones por días y horarios.

Moderación y administración. Un panel administrativo interno permite gestionar perfiles, pagos, verificaciones, denuncias y estadísticas. El sistema de denuncias encripta la información sensible del denunciante y clasifica los reportes por tipo y estado. Existe un rol de moderador con permisos limitados.

SEO y visibilidad. El sistema genera automáticamente datos estructurados (Schema.org), gestiona la indexación de perfiles según su antigüedad y estado, y construye rutas amigables con breadcrumbs dinámicos.

Tareas programadas. Un gestor centralizado de tareas cron coordina procesos periódicos como limpieza de datos expirados, recálculo de conteos, envío de notificaciones y mantenimiento general, con auto-reparación de tareas perdidas.

Temas y frontend. La capa visual utiliza un tema padre con temas hijos por país, permitiendo personalizar la identidad visual de cada operación manteniendo una base de código compartida. Los componentes de interfaz son modulares y reutilizables a través de un sistema de registro con configuración en JSON.
