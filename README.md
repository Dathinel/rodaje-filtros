<p align="center">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://raw.githubusercontent.com/Dathinel/rodaje/main/assets/marca/rodaje.svg" alt="Logotipo de Rodaje" width="104"></a>
</p>

<h1 align="center">rodaje-filtros</h1>

<p align="center">
  Complemento opcional para <a href="https://github.com/Dathinel/rodaje">Rodaje</a>: 13 looks de color, cada uno un filtro con su LUT 3D (33³), generadas por fórmulas propias.
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/licencia-CC0_1.0-E8833A?style=flat-square&labelColor=1D1D1D" alt="Licencia CC0 1.0"></a>
  <a href="https://github.com/Dathinel/rodaje-filtros/releases/latest"><img src="https://img.shields.io/github/v/release/Dathinel/rodaje-filtros?style=flat-square&labelColor=1D1D1D&color=E8833A&label=versi%C3%B3n" alt="Última versión"></a>
  <img src="https://img.shields.io/badge/contenido-13_looks-E8833A?style=flat-square&labelColor=1D1D1D" alt="Contenido: 13 looks">
  <img src="https://img.shields.io/badge/formato-.paquete-E8833A?style=flat-square&labelColor=1D1D1D" alt="Formato .paquete">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://img.shields.io/badge/para-Rodaje-E8833A?style=flat-square&labelColor=1D1D1D" alt="Para Rodaje"></a>
</p>

Los looks: cálido, frío, verde azulado y naranja, blanco y negro, desvaído, vivo, noche, cine (con viñeta), sepia, alto contraste, pastel, cian suave y plata (blanqueo parcial). Las LUT salen de fórmulas propias en `generar.ps1` (curva en S, saturación sobre la luminancia Rec. 709 y desplazamientos por canal según la luminancia); no hay LUT ni recursos de terceros.

## Instalar en Rodaje

En Rodaje, Complementos → Instalar lo baja, comprueba su firma y lo instala. A mano: descarga `rodaje-filtros-<versión>.paquete` de las [releases](https://github.com/Dathinel/rodaje-filtros/releases) y, en Rodaje, usa «Instalar desde archivo…» en Complementos o suéltalo sobre la biblioteca. Los looks aparecen en Filtros; las LUT sueltas también, para usarlas con la intensidad que quieras. Más detalles en la [guía de complementos](https://github.com/Dathinel/rodaje/blob/main/docs/guia/complementos.md).

## Construir el paquete

```
powershell -NoProfile -ExecutionPolicy Bypass -File empaquetar.ps1
```

Solo hace falta Windows PowerShell 5.1. Genera las LUT, comprueba que existan todos los archivos del manifiesto y deja `dist\rodaje-filtros-<versión>.paquete` con orden y fecha fijos: las mismas fuentes dan el mismo archivo byte a byte. `-Salida <carpeta>` cambia dónde queda.

| Archivo | Qué es |
|---|---|
| `paquete.json` | Manifiesto: 13 `filter` y 13 `lut` |
| `filtros/*.json` | `rodaje.filter` v1: `rodaje.color` con su LUT (`./lut-<look>`, de este mismo paquete) |
| `generar.ps1` | Las fórmulas de los looks; escribe `luts/*.cube` |
| `empaquetar.ps1` | Arma el `.paquete` |

## Licencia

CC0 1.0 (dominio público), ver `LICENSE`. El logotipo de Rodaje es marca de su autor y no forma parte de este contenido ([TRADEMARK.md](https://github.com/Dathinel/rodaje/blob/main/TRADEMARK.md)).
