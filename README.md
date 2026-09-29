# AutoResearchGraph

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21627938.svg)](https://doi.org/10.5281/zenodo.21627938)

**Aplicación:** https://fborrasumh.github.io/autoresearchgraph/

Mejora un documento (una memoria, una propuesta, un informe, un artículo) **con un cambio comprobado cada vez**. Un evaluador de IA lo puntúa con tus criterios, otro agente propone un cambio pequeño y el cambio solo se queda si mejora de verdad y no estropea nada. Cada intento, bueno o malo, queda registrado en un grafo. Aplicación de un solo fichero (`index.html`), sin servidor.

## Novedades de la versión 2.0

- Recorrido guiado con el estilo de Forja: **Inicio → Documento → Criterios → Mejorar → Resultado**.
- **Tres intensidades** (Rápida, Equilibrada y A fondo) en lugar de doce parámetros. Los parámetros siguen disponibles en «Ajustes avanzados», explicados en castellano.
- **Sin jerga en la interfaz**: el procedimiento se explica en cuatro pasos y las defensas contra las trampas, en dos.
- **Ejemplos**:
  - una mejora completa de muestra que se ve sin clave, con cambios conservados, un relleno deshecho por el criterio oculto, un parche no aplicable y un cambio bloqueado por tocar un texto protegido;
  - dos documentos de prueba que cargan sus criterios y sus textos protegidos.
- Se puede **pegar el texto** además de subir un archivo.
- **Evaluador económico por defecto** (gpt-4o-mini en lugar de gpt-4o), distinto del modelo que propone los cambios.
- El resultado muestra el documento, los cambios conservados uno a uno y la variación de cada criterio. Todos los intentos, el grafo, las búsquedas, el aprendizaje y los prompts quedan en secciones plegadas.
- Corregido: al cambiar de documento quedaban los datos de la ejecución anterior.

## Cómo decide si un cambio se queda

1. **Se mide.** El evaluador puntúa cada criterio varias veces y se toma la mediana.
2. **Se propone.** Otro agente cambia un fragmento concreto (formato parche) para mejorar el criterio más flojo; nunca reescribe el documento entero.
3. **Tres filtros.** El cambio tiene que mejorar la nota lo suficiente, ningún criterio puede empeorar más de lo permitido y un juez que no sabe cuál es la versión nueva tiene que preferirla en 2 de 3 votos.
4. **Se queda o se deshace.** Los cambios deshechos se recuerdan para no repetirlos y forman parte del grafo de intentos.

## Defensas contra las trampas

- **Criterios ocultos**: el evaluador los puntúa, pero el agente que cambia el texto no los ve (por defecto, «sin relleno»). Si la nota visible sube y la oculta baja, la app avisa.
- **Textos protegidos**: cifras, nombres o citas que se comprueban con código tras cada cambio. Si alguno desaparece o cambia, el cambio se deshace sin gastar consultas.

## Origen

Inspirada en *autoresearch* de Andrej Karpathy y en la idea de AgentHub de tratar los experimentos como un grafo.

## Privacidad

El documento se procesa en el navegador. El texto viaja a OpenAI con la clave del usuario, guardada en `localStorage` (`ia_openai_key`). Si se activa la búsqueda de evidencia, las consultas van a Crossref, PubMed, OpenAlex y Wikipedia, o a Tavily con su propia clave.

## Cómo citar

Borrás Rocher, F. (2026). *AutoResearchGraph* (versión 2.0.0) [Software]. Universidad Miguel Hernández de Elche. https://doi.org/10.5281/zenodo.21627938

El DOI es el de concepto: apunta siempre a la última versión. GitHub ofrece la cita en APA y BibTeX con el botón *Cite this repository*, a partir de `CITATION.cff`.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche.
