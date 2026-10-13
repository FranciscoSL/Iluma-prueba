# Nota sobre el uso de IA

**Dónde usé IA y para qué**
- Usé un asistente de código (Claude Code) para revisar los cuatro archivos, proponer los chequeos de calidad de datos y escribir los dos notebooks (limpieza y análisis).
- También lo usé para redactar un primer borrador de este README.
- Lo usé como "analista de compras" de reemplazo para armar la lista de preguntas que le haría al negocio.
- Una primera versión usaba técnicas más avanzadas: interpolación de precios por fecha y simulación diaria de la bodega. Le pedí rehacerla con funciones de pandas que conozco y puedo explicar (`merge`, `groupby`, `np.where`, `pivot_table`).

**Dónde decidí no depender de la IA**
- **Los supuestos.** El 50% de castigo por vencimiento, la capacidad compartida, excluir las 3 órdenes que superan la capacidad y poner en 0 los días de los servicios son decisiones de criterio. Quedan escritas en los notebooks para poder discutirlas.
- **Verificar el número principal.** Recalculé a mano el ejemplo PO10041-S desde los datos originales: 4,10 + 601,32/1.875 + 0,0579 × 137 + 0,5 × 4,10 = 14,40, contra 5,71 por contrato.

**Lo que la IA hizo mal o incompleto**
- Generó código de gráficos que no funcionaba con mi versión de matplotlib y una conversión de fechas obsoleta. Hubo que corregirlos.
- El primer borrador del informe tenía cifras que no coincidían exactamente con las tablas: el porcentaje de ocupación Spot de un centro y el rango del descuento contra el benchmark. Las corregí comparando con las salidas del notebook.
- Tomó las tarifas de almacenamiento como correctas sin cuestionarlas. Implican que guardar materias primas cuesta ~1,2% de su valor por día. Por eso agregué la prueba de sensibilidad con la mitad de la tarifa: es el dato del que más depende la conclusión.
