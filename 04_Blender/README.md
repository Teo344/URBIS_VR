# Blender – convenciones (empezar después del levantamiento)

- **Escala:** 1 unidad = 1 m. Aplicar rotación y escala (Ctrl+A) antes de exportar.
- **Prefijos:** `LAB_` arquitectura · `MOB_` mobiliario · `INT_` interactivos (objetos separados) · `SEN_` señalética · `COL_` colisiones simplificadas.
- **Pivotes:** puerta en la bisagra, extintor en la base, pulsador al centro.
- **Materiales:** solo Principled BSDF (Base Color, Roughness, Metallic, Normal, Emission). Lo procedural se hornea a textura. Usar pocos materiales compartidos.
- **UV2** sin solapamientos para hornear luz (lightmaps) en Unity.
- **Presupuesto Quest (orientativo):** 300k–500k triángulos en toda la escena, texturas de 1K–2K en atlas.
- **Exportación:** FBX en `export/` con *Apply Transform*, *Forward −Z*, *Up Y*. Un archivo por grupo (`LAB`, `MOB`, `INT`, `SEN`).
- **Fases:** 1) blockout a escala → probar en el visor · 2) modelado final · 3) UV + materiales · 4) exportación.
- El fuego y el humo **no** se modelan aquí: se hacen con partículas en Unity.
