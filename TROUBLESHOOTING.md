# 🛠️ Solución de Problemas de Markdown

Esta guía está diseñada para ayudarte a identificar y resolver los problemas más comunes que puedes encontrar al trabajar con Markdown en diferentes plataformas y contextos.

## Problemas de Formato Básico

### Problema: Los párrafos no tienen separación

**Síntomas:**
El texto que debería estar en párrafos separados aparece junto.

**Solución:**
Asegúrate de dejar una línea en blanco entre párrafos:

```markdown
Este es el primer párrafo.

Este es el segundo párrafo con correcta separación.
```

**Explicación:**
Markdown requiere una línea en blanco para indicar un nuevo párrafo. Sin ella, el texto se considera parte del mismo párrafo.

---

### Problema: Los saltos de línea simples se ignoran

**Síntomas:**
Al presionar Enter una vez para hacer un salto de línea, el texto sigue en la misma línea al renderizarse.

**Soluciones:**
1. **Opción 1:** Añade dos espacios al final de la línea donde quieres el salto:
   ```markdown
   Primera línea··  
   Segunda línea
   ```
   (donde `··` representa espacios)

2. **Opción 2:** Usa la etiqueta HTML `<br>`:
   ```markdown
   Primera línea<br>
   Segunda línea
   ```

**Explicación:**
Por diseño, Markdown ignora un solo salto de línea para permitir que el texto fuente tenga saltos por legibilidad sin afectar el resultado.

---

### Problema: El énfasis (negrita/cursiva) no funciona

**Síntomas:**
El texto que marcaste con asteriscos o guiones bajos aparece con los símbolos visibles en lugar de con formato.

**Soluciones:**
1. **Espaciado incorrecto:** No debe haber espacios entre los asteriscos/guiones y el texto.
   - ❌ `* texto *`
   - ✅ `*texto*`

2. **Mezclando símbolos:** Usa el mismo símbolo para abrir y cerrar.
   - ❌ `*texto_`
   - ✅ `*texto*` o `_texto_`

3. **Escape en medio:** Si tienes asteriscos dentro del texto a enfatizar:
   ```markdown
   *texto con un \* asterisco*
   ```

4. **Saltos de línea:** El énfasis no puede contener saltos de párrafo:
   ```markdown
   *Este formato
   
   no funcionará*
   ```

---

## Problemas con Listas

### Problema: Las listas anidadas no funcionan correctamente

**Síntomas:**
Los subelementos de una lista aparecen al mismo nivel que los elementos principales.

**Soluciones:**
1. **Indentación correcta:** Usa 4 espacios o 1 tab para cada nivel de anidamiento:
   ```markdown
   - Elemento principal
       - Subelemento (4 espacios antes)
           - Sub-subelemento (8 espacios antes)
   ```

2. **Líneas en blanco:** Algunas implementaciones requieren líneas en blanco:
   ```markdown
   - Elemento principal
   
       - Subelemento con línea en blanco antes
   ```

3. **Consistencia:** Usa el mismo tipo de indentación en todo el documento.

---

### Problema: Las listas numeradas no se renumeran automáticamente

**Síntomas:**
Cuando reordenas elementos en una lista numerada, los números en el resultado final no se actualizan.

**Soluciones:**
1. **Uso de 1.** en todas las entradas para renumeración automática:
   ```markdown
   1. Primer elemento
   1. Segundo elemento (aparecerá como 2)
   1. Tercer elemento (aparecerá como 3)
   ```

2. **Numeración explícita** si tu procesador de Markdown no renumera automáticamente:
   ```markdown
   1. Primer elemento
   2. Segundo elemento
   3. Tercer elemento
   ```

---

## Problemas con Enlaces e Imágenes

### Problema: Los enlaces no funcionan

**Síntomas:**
Los enlaces aparecen como texto normal o muestran la sintaxis de Markdown en lugar de funcionar como enlaces.

**Soluciones:**
1. **Verifica la sintaxis básica:**
   ```markdown
   [Texto del enlace](URL)
   ```

2. **Enlaces con paréntesis:** Si la URL contiene paréntesis, escápalos:
   ```markdown
   [Ejemplo](https://ejemplo.com/ruta\(con\)paréntesis)
   ```

3. **Espacios en URLs:** Codifica los espacios como `%20` o encierra la URL entre `<` y `>`:
   ```markdown
   [Enlace](https://ejemplo.com/ruta%20con%20espacios)
   [Enlace](<https://ejemplo.com/ruta con espacios>)
   ```

4. **Enlaces con caracteres especiales:** Asegúrate de que los caracteres especiales en la URL estén codificados correctamente.

---

### Problema: Las imágenes no se muestran

**Síntomas:**
En lugar de la imagen, aparece el texto alternativo o la sintaxis de Markdown.

**Soluciones:**
1. **Verifica la sintaxis:**
   ```markdown
   ![Texto alternativo](ruta/a/la/imagen.jpg)
   ```

2. **Verifica la ruta:**
   - **Rutas relativas:** ¿Es correcta en relación al documento?
   - **URLs:** ¿Está la imagen accesible públicamente?
   - **Permisos:** ¿La plataforma permite embeber imágenes externas?

3. **Formatos de imagen:** Asegúrate de usar formatos compatibles (generalmente PNG, JPEG, GIF, SVG).

4. **Plataformas restrictivas:** Algunas plataformas solo permiten imágenes de ciertos dominios o requieren subir las imágenes a su servicio.

---

## Problemas con Tablas

### Problema: Las tablas se muestran mal formateadas

**Síntomas:**
Las columnas no se alinean o la tabla aparece como texto plano.

**Soluciones:**
1. **Sintaxis correcta:** Asegúrate de tener al menos una línea de encabezado, la línea separadora y filas de datos:
   ```markdown
   | Encabezado 1 | Encabezado 2 |
   |-------------|-------------|
   | Dato 1      | Dato 2      |
   ```

2. **Mismo número de columnas:** Todas las filas deben tener el mismo número de separadores `|`.

3. **Línea separadora:** Debe contener al menos 3 guiones (`---`) por columna.

4. **Generadores de tablas:** Usa herramientas como [Tables Generator](https://www.tablesgenerator.com/markdown_tables) para crear tablas complejas.

---

### Problema: No se pueden alinear datos en las tablas

**Síntomas:**
El contenido no se alinea según lo deseado (izquierda, centro, derecha).

**Solución:**
Usa `:` en la línea separadora para indicar la alineación:

```markdown
| Izquierda | Centro | Derecha |
|:---------|:-------:|--------:|
| Texto    | Texto   | Texto   |
```

**Explicación:**
- `:---` alinea a la izquierda (predeterminado)
- `:---:` alinea al centro
- `---:` alinea a la derecha

---

## Problemas con Código

### Problema: El resaltado de sintaxis no funciona

**Síntomas:**
El código aparece sin colores o con colores incorrectos.

**Soluciones:**
1. **Especifica el lenguaje:** Añade el nombre del lenguaje después de las primeras comillas invertidas:
   ````markdown
   ```javascript
   function ejemplo() {
     console.log("Hola mundo");
   }
   ```
   ````

2. **Lenguaje soportado:** Verifica que la plataforma soporte el lenguaje que estás usando.

3. **Nombres alternativos:** Algunos procesadores usan nombres diferentes para los mismos lenguajes:
   - `js` vs `javascript`
   - `py` vs `python`

---

### Problema: Los bloques de código no aparecen correctamente

**Síntomas:**
El código aparece en línea o con formato incorrecto.

**Soluciones:**
1. **Indentación correcta:** Para bloques de código con indentación, usa 4 espacios o 1 tab.

2. **Bloques delimitados:** Para bloques con comillas invertidas, asegúrate de usar tres comillas invertidas al inicio y final:
   ````markdown
   ```
   Código aquí
   ```
   ````

3. **Líneas en blanco:** Añade líneas en blanco antes y después del bloque de código.

4. **Escape de comillas invertidas:** Si necesitas mostrar comillas invertidas dentro del bloque, usa más comillas en los delimitadores:
   `````markdown
   ````
   ```
   Código con comillas invertidas
   ```
   ````
   `````

---

## Problemas con Dialectos y Plataformas Específicas

### Problema: Características que funcionan en una plataforma pero no en otra

**Síntomas:**
Elementos como tachado, listas de tareas o tablas funcionan en GitHub pero no en otras plataformas.

**Soluciones:**
1. **Conoce el dialecto:** Identifica qué "sabor" de Markdown usa cada plataforma:
   - GitHub usa GitHub Flavored Markdown
   - Reddit usa una variante personalizada
   - Discord tiene su propia implementación

2. **Sintaxis universal:** Cuando sea posible, usa solo características del "Core Markdown" o CommonMark:
   - Encabezados
   - Párrafos
   - Énfasis básico
   - Enlaces simples
   - Listas básicas

3. **Previsualiza:** Usa la función de vista previa si está disponible antes de publicar.

4. **Consulta la documentación** específica de cada plataforma.

---

### Problema: Formateo HTML no permitido o filtrado

**Síntomas:**
Las etiquetas HTML aparecen como texto o son eliminadas.

**Soluciones:**
1. **Verifica la política:** Algunas plataformas no permiten HTML por razones de seguridad.

2. **Alternativas en Markdown puro:**
   - Para colores: No hay alternativa directa, usa descripciones textuales
   - Para alineación: Usa tablas o espaciado estratégico
   - Para formato avanzado: Busca extensiones específicas de la plataforma

3. **HTML permitido:** Si la plataforma lo permite, usa solo etiquetas seguras como:
   - `<span>`, `<div>`
   - `<strong>`, `<em>`
   - `<sub>`, `<sup>`
   - `<details>`, `<summary>`

---

## Problemas de Conversión y Exportación

### Problema: La conversión a PDF u otros formatos falla

**Síntomas:**
Al usar herramientas como Pandoc, la conversión falla o produce resultados incorrectos.

**Soluciones:**
1. **Markdown válido:** Verifica que tu documento Markdown esté bien formado.

2. **Dependencias:** Asegúrate de tener todas las dependencias necesarias:
   - Para PDF: LaTeX (como TeX Live o MiKTeX)
   - Para DOCX: No se necesitan dependencias adicionales
   - Para presentaciones: El motor de presentación apropiado

3. **Opciones específicas de formato:**
   ```bash
   # Para PDF con márgenes personalizados
   pandoc input.md -o output.pdf -V geometry:"margin=1in"
   
   # Para DOCX con una plantilla de estilo
   pandoc input.md -o output.docx --reference-doc=template.docx
   ```

4. **Fragmenta el documento:** Si es muy grande o complejo, intenta convertir partes por separado.

---

### Problema: Las imágenes faltan en los documentos convertidos

**Síntomas:**
Después de la conversión, las imágenes no aparecen en el documento final.

**Soluciones:**
1. **Rutas absolutas:** Usa rutas absolutas para las imágenes o asegúrate de que las relativas sean correctas desde donde se ejecuta la conversión.

2. **Incluye recursos:**
   ```bash
   # Para Pandoc, especifica el directorio de recursos
   pandoc input.md -o output.pdf --resource-path=./images
   ```

3. **Formatos soportados:** Asegúrate de que el formato de destino soporte los formatos de imagen que usas.

---

## Mejores Prácticas para Evitar Problemas

1. **Usa un linter:** Herramientas como `markdownlint` pueden detectar problemas comunes.
   
2. **Previsualiza siempre:** Muchos editores ofrecen previsualización en tiempo real.

3. **Conoce tu plataforma:** Familiarízate con las peculiaridades de la plataforma donde publicarás.

4. **Mantén copias de respaldo:** Especialmente antes de conversiones o publicaciones importantes.

5. **Valida con herramientas:** Servicios como [CommonMark Dingus](https://spec.commonmark.org/dingus/) pueden ayudarte a verificar tu Markdown.

6. **Automatiza pruebas:** Para proyectos grandes, considera integrar validadores de Markdown en tu flujo de trabajo.

7. **Mantén la consistencia:** Usa el mismo estilo y convenciones en todo tu documento o proyecto.

---

Si encuentras problemas que no están cubiertos en esta guía, consulta:
- La [documentación oficial](https://daringfireball.net/projects/markdown/) de Markdown
- La especificación [CommonMark](https://commonmark.org/)
- La documentación específica de la plataforma que estés utilizando
- Comunidades como [Stack Overflow](https://stackoverflow.com/questions/tagged/markdown)

**Última actualización:** 8 de julio de 2025
