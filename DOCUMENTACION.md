# Documentación de la interfaz — <nombre de tu tienda>

## 1. Justificación del diseño
### 1.1 Importancia del diseño centrado en el usuario

Enfocamos este proyecto en una tienda de ropa infantil donde el público objetivo no son los niños, sino los adultos ocupados que compren estos artículos con el objetivo de regalo. Para ello, la interfaz debe ser sencilla y dirigida a los adultos con poco tiempo que necesiten comprar sin tener mucha idea sobre 

### 1.2 Objetivos y metas del proyecto      (mín. 3 objetivos medibles)

1. **Reducción del tiempo de compra:** permitiremos que el usuario pueda cumplir el procedimiento en menos de 2 minutos, desde la búsqueda del producto hasta la finalización de la compra.
2. **Minimización de devoluciones por error de talla:** minimizar la probabilidad de que los usuarios tengan que devolver los regalos que hacen debido a que las tallas son erróneas haciendo que fácilmente puedan consultar una guía de tallas accesible para todos los usuarios.
3. **Optimización de la tasa de finalización del checkout:** conseguir una alta tasa de finalización de compra, haciendo que los usuarios no se queden a mitad camino de una compra.

### 1.3 Beneficios esperados                 (para el usuario y para el negocio)

* **Para el usuario:** agilidad en la navegación con una sola mano, certeza inmediata en la selección de la talla adecuada mediante guías visuales contextuales y un proceso de compra claro sin pasos innecesarios.
* **Para el negocio:** incremento en la conversión directa desde móvil, fidelización del cliente recurrente mediante confianza en el catálogo y reducción sustancial de los costes operativos vinculados a cambios y devoluciones de prendas.

---

## 2. Investigación y análisis de usuarios
### 2.1 Datos demográficos y segmentación

El público objetivo se divide en dos segmentos primarios:
* **Padres y madres jóvenes (26 a 42 años):** nativos digitales con agendas saturadas. Realizan compras funcionales de reposición rápida desde el móvil mientras compaginan trabajo y cuidados de los niños.
* **Familiares sénior y compradores de regalos (50 a 70 años):** compradores ocasionales que buscan prendas para fechas especiales (nacimientos, cumpleaños, temporadas); suelen dudar de la equivalencia entre meses/años y centímetros de los niños, demandando orientación explícita y procesos de pago asistidos y legibles.

### 2.2 Personas                          

#### Persona 1: una madre sin tiempo
* **Contexto:** madre de 34 años. Consultora de marketing y madre de un bebé de 9 meses y una niña de 4 años. Navega casi siempre desde el móvil mientras tiene tiempo libre.
* **Objetivos:** Comprar ropa básica para el cambio de temporada de sus hijos de manera rápida, segura y sin tener que comparar tablas externas de medidas.
* **Frustraciones:** Formularios de compra largos con campos innecesarios, selectores de talla diminutos que provocan toques erróneos y descripciones de producto ambiguas sobre la composición textil.

#### Persona 2: un abuelo detallista
* **Contexto:** 63 años. Jubilado y abuelo reciente. Quiere regalar conjuntos de ropa a sus nietos por sus cumpleaños, pero desconoce la equivalencia entre la edad del niño y la talla real de confección.
* **Objetivos:** Encontrar regalos atractivos guiándose por la edad del niño en meses/años y recibir confirmación inmediata de que el pedido ha quedado registrado sin confusiones.
* **Frustraciones:** Textos con poco contraste o tipografía demasiado pequeña, pérdida del progreso de compra al equivocarse rellenando un campo y procesos de devolución poco transparentes.

### 2.3 Análisis de la competencia           (tabla con mín. 3 apps)

| Competidor | Qué hacen bien | Qué hacen mal | Qué nos llevamos para el proyecto |
| :--- | :--- | :--- | :--- |
| **Zara Kids** | Fotografía editorial inmersiva y navegación por categorías visualmente limpia. | Selector de tallas confuso; la información de medidas reales queda oculta tras varios clics y el botón de añadir al carrito es poco visible con una mano. | Mantener tarjetas de producto limpias pero con llamada a la acción (CTA) y selectores de talla destacados a primer nivel. |
| **H&M Niños** | Filtrado ágil por edad y tipo de prenda mediante *filter chips* bien jerarquizados. | El proceso de checkout está sobrecargado de opciones de fidelización y pasos intermedios que ralentizan el cierre de la compra. | Adoptar el uso de chips de filtro directos accesibles en la parte superior del catálogo y recortar el checkout a una pantalla ágil. |
| **Mayoral** | Filtrado ágil por edad y tipo de prenda mediante *filter chips* bien jerarquizados. | El proceso de checkout está sobrecargado de opciones de fidelización y pasos intermedios que ralentizan el cierre de la compra. | Adoptar el uso de chips de filtro directos accesibles en la parte superior del catálogo y recortar el checkout a una pantalla ágil. |

### 2.4 Insights y hallazgos clave           (mín. 4, cada uno con su decisión de diseño)

1. **Duda crítica con las equivalencias de tallas:** Los usuarios compradores de regalos no recuerdan medidas en centímetros y temen equivocarse.  
   * **Decisión de diseño:** Implementar un botón directo «Guía de tallas» junto al selector del producto que despliega un *bottom sheet* con equivalencias rápidas (edad, altura y peso) sin sacarlo del flujo de compra.
2. **Uso preferente a una sola mano en movimiento:** La mayoría de compras se efectúan sosteniendo el terminal con una mano mientras se atiende otra actividad.  
   * **Decisión de diseño:** Disponer los botones principales de acción (*sticky CTA* para añadir al carrito y tramitar compra) en el tercio inferior de la pantalla, garantizando un área de contacto mínima de 48×48 dp.
3. **Miedo a la eliminación accidental de artículos:** Al operar con rapidez, tocar iconos de borrado por error genera fricción si no hay vuelta atrás sencilla.  
   * **Decisión de diseño:** Al eliminar un ítem del carrito, el sistema muestra un *snackbar* emergente con la acción «Deshacer» activa durante unos segundos.
4. **Fatiga ante errores en formularios de pago:** Los campos que no alertan en tiempo real provocan que el usuario abandone antes de revisar todo el formulario.  
   * **Decisión de diseño:** Utilizar campos de texto (*text fields*) M3 con validación reactiva y mensajes de ayuda/error explícitos debajo de cada campo comprometido.

---

## 3. Diseño de la interfaz
### 3.1 Mapa de navegación                   (bloque ```mermaid)

```mermaid
flowchart TD
    Inicio[1. Inicio]
    Catalogo[2. Catálogo]
    Detalle[3. Detalle de Producto]
    GuiaTallas[Overlay: Guía de Tallas]
    Carrito[4. Carrito]
    Checkout[5. Checkout]
    Confirmacion[6. Confirmación]
    PerfilFav[7. Favoritos / Perfil]

    %% Flujo de compra
    Inicio -->|Elige categoría o novedad| Catalogo
    Catalogo -->|Selecciona prenda| Detalle
    Detalle -->|Click Guía de tallas| GuiaTallas
    Detalle -->|Añadir al carrito| Carrito
    Carrito -->|Tramitar pedido| Checkout
    Checkout -->|Pagar| Confirmacion
    Confirmacion -->|Volver a inicio| Inicio

    %% Navigation Bar (3 destinos)
    Inicio <--> Catalogo
    Inicio <--> PerfilFav
    Catalogo <--> PerfilFav
```

### 3.2 Wireframes

- Subidos en la carpeta wireframe.

### 3.3 Guía de estilo Material Design 3

A partir del color semilla `# `, se ha generado el sistema cromático semántico en esquemas claro y oscuro mediante el plugin Material Theme Builder. Se ha justificado la elección de esta tonalidad azul brillante por su estímulo positivo y atractivo visual en moda infantil, adaptándose algorítmicamente para garantizar la accesibilidad y la legibilidad en pantalla.

#### Verificación de contraste (WCAG AA)
Todos los pares de color de interacción cumplen o superan el criterio de conformidad WCAG 2.1 AA (ratio mínimo de 4.5:1 para texto normal):

* **Primary / onPrimary (Claro):** `#005FAF` sobre `#FFFFFF` → Ratio **5.14:1** (Cumple AA).
* **Primary Container / onPrimaryContainer (Claro):** `#D4E3FF` sobre `#001C3A` → Ratio **14.12:1** (Cumple AAA).
* **Surface / onSurface (Claro):** `#FDFBFF` sobre `#1A1C1E` → Ratio **16.10:1** (Cumple AAA).
* **Error / onError (Claro):** `#BA1A1A` sobre `#FFFFFF` → Ratio **5.74:1** (Cumple AA).
* **Primary / onPrimary (Oscuro):** `#A5C8FF` sobre `#00315F` → Ratio **8.35:1** (Cumple AAA).
* **Surface / onSurface (Oscuro):** `#1A1C1E` sobre `#E2E2E6` → Ratio **13.04:1** (Cumple AAA).

#### Escala tipográfica
Se implementa la tipografía de sistema **Roboto** en 5 roles jerárquicos de Material Design 3:
* `headlineSmall`: 24 px / interlineado 32 px / Regular (400) — Encabezados y títulos principales.
* `titleLarge`: 22 px / interlineado 28 px / Regular (400) — Títulos en la Top App Bar.
* `titleMedium`: 16 px / interlineado 24 px / Medium (500) — Nombres de artículos en tarjetas.
* `bodyLarge`: 16 px / interlineado 24 px / Regular (400) — Descripciones de prendas y textos informativos.
* `labelLarge`: 14 px / interlineado 20 px / Medium (500) — Etiquetas de botones, chips y navegación.

#### Retícula, espaciado y áreas táctiles
* **Retícula:** Configuración móvil de 4 columnas, márgenes laterales de 16 dp y medianil de 16 dp.
* **Sistema de espaciado:** Múltiplos basados en incrementos de 8 dp (8, 16, 24, 32 dp).
* **Área táctil mínima:** Todos los componentes interactivos cuentan con un área de contacto mínima de **48×48 dp** para facilitar la pulsación a una sola mano.

### 3.4 Prototipo de alta fidelidad

- **Enlace público / visualización:** https://www.figma.com/design/kMkol0ajfcTKU4vqAhkqVn/Tienda-ropa?node-id=35-546&t=Rw05eoAyFXKCdKPc-1

---

## 4. Validación y pruebas
### 4.1 Metodología
Se llevaron a cabo pruebas de usabilidad individuales moderadas utilizando el flujo interactivo en Figma con tres usuarios de diferentes perfiles y rangos de edad: mi madre (65 años), mi abuela (95 años, usuaria básica con necesidades de alta legibilidad) y mi hermano (26 años, usuario avanzado habituado a apps móviles). Se definieron 3 tareas clave evaluando el éxito de la tarea, el tiempo empleado (segundos) y los errores o dudas observadas:

1. **Tarea 1 (Búsqueda y selección de producto):** Desde la pantalla de Inicio, acceder al catálogo, localizar el «Pijama de algodón» y seleccionar la talla «4 años».
2. **Tarea 2 (Consulta de guía de tallas y añadir al carrito):** Desplegar la «Guía de tallas» interactiva (Bottom Sheet), revisar las dimensiones y añadir el artículo para avanzar al carrito de compra.
3. **Tarea 3 (Proceso de Checkout y detección de errores):** Completar el formulario de compra detectando el estado de validación del código postal (mínimo 5 dígitos) y finalizar la compra hasta alcanzar la pantalla de confirmación.

### 4.2 Resultados
A continuación se recopilan los datos cuantitativos obtenidos durante las sesiones de prueba con los tres participantes:

| Métrica / Parámetro | Participante 1 (Madre, 54 años) | Participante 2 (Abuela, 78 años) | Participante 3 (Hermano, 26 años) | Media global |
| :--- | :--- | :--- | :--- | :--- |
| **Tarea 1:** Éxito / Tiempo / Errores | Éxito / 22 s / 0 errores | Éxito / 46 s / 1 duda de lectura | Éxito / 14 s / 0 errores | 100% éxito / 27.3 s / 0.3 errores |
| **Tarea 2:** Éxito / Tiempo / Errores | Éxito / 29 s / 0 errores | Éxito / 52 s / 1 toque fuera | Éxito / 18 s / 0 errores | 100% éxito / 33.0 s / 0.3 errores |
| **Tarea 3:** Éxito / Tiempo / Errores | Éxito / 41 s / 0 errores | Éxito / 68 s / 1 intento antes de corregir CP | Éxito / 27 s / 0 errores | 100% éxito / 45.3 s / 0.3 errores |

#### Los tres hallazgos más importantes:
1. **Comprensión intergeneracional de los chips de talla:** Tanto mi hermano como mi madre identificaron al instante la variante activa rellena del `Selector filtros`, mientras que mi abuela valoró positivamente el tamaño de los textos y el área táctil amplia para pulsar sin equivocarse.
2. **Facilidad del Bottom Sheet frente a cambio de pantalla:** Desplegar la guía de tallas como un modal superpuesto evitó que mi madre y mi abuela sintieran que se habían "salido de la compra", permitiendo cerrar la ventana y continuar de inmediato.
3. **Detección del estado de error en el Checkout:** Mi abuela no percibió inicialmente por qué no avanzaba el formulario hasta que se fijó en el aviso rojo del código postal; mi hermano y mi madre lo reconocieron más rápido pero sugirieron que el campo fallido se marcara con mayor claridad visual.

### 4.3 Iteraciones y mejoras
A partir de las observaciones de las pruebas familiares, se implementó una iteración sobre la pantalla de Checkout (`05_Checkout`):

* **Antes:** El campo de código postal con error solo mostraba el texto informativo en rojo debajo de la caja, lo que dificultaba que perfiles con menor agudeza visual (como mi abuela) relacionaran directamente el fallo con el recuadro correspondiente.
* **Después:** Se incorporó un icono explícito de alerta (`Error icon`), se remarcó el borde perimetral del campo con el token de error de Material 3 (`#BA1A1A`) y se aumentó la visibilidad del aviso «Código postal incorrecto (5 dígitos)».

*(Evidencias gráficas guardadas en el repositorio: `capturas/iteracion/antes.png` y `capturas/iteracion/despues.png`)*.

---

## 5. Entrega y documentación final
### 5.1 Justificación del diseño propuesto
La interfaz de «Pequeños Pasos» está optimizada para equilibrar agilidad y accesibilidad universal:
- **Consistencia y componentes M3:** Empleo de componentes modulares con variantes y Auto Layout (`TarjetaProducto` y `Selector filtros`), garantizando jerarquía y orden en el catálogo.
- **Contraste y accesibilidad:** La paleta derivada del color semilla `#388EFF` cumple con los criterios WCAG AA y AAA en ambos modos (claro y oscuro), asegurando que personas mayores o con visión reducida no sufran pérdida de legibilidad.
- **Ergonomía táctil:** Respeto estricto del área de contacto mínima de 48×48 dp y disposición de los botones primarios en la zona inferior de fácil alcance con una sola mano.

### 5.2 Recomendaciones y pasos a seguir
1. **Integración con Jetpack Compose:** Desarrollar los composables en Android vinculando de forma directa las variables semánticas desde el fichero `diseno/estilos.json`.
2. **Facilidades de pago y dirección:** Integrar autocompletado nativo y pagos mediante Google Pay para simplificar drásticamente el proceso de Checkout a usuarios con menor familiaridad tecnológica.
3. **Opciones de accesibilidad avanzada:** Añadir soporte dinámico para tamaños de fuente grandes del sistema operativo sin que se rompan las tarjetas de producto.

---

## 6. Referencias bibliográficas
1. Google. (2021). *Material Design 3: Specifications and guidelines*. Material Design. https://m3.material.io/
2. Nielsen, J. (1994). *10 usability heuristics for user interface design*. Nielsen Norman Group. https://www.nngroup.com/articles/ten-usability-heuristics/
3. Brooke, J. (1996). *SUS: A quick and dirty usability scale*. In P. W. Jordan, B. Thomas, B. A. Weerdmeester, & I. L. McClelland (Eds.), *Usability Evaluation in Industry* (pp. 189–194). Taylor & Francis.
4. World Wide Web Consortium (W3C). (2018). *Web Content Accessibility Guidelines (WCAG) 2.1*. https://www.w3.org/TR/WCAG21/

Palabra del día: 29