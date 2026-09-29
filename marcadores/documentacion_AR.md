# Documentación Oficial: Sistema de Marcadores AR para Proiectio (Capítulos 1-13 + Expansión 14-24)

Este documento detalla la arquitectura, codificación y montaje de la capa de Realidad Aumentada (WebAR) para el universo de *Proiectio / Cloto*.

---

## 1. Los Marcadores Físicos (Imágenes PNG)
Dentro de esta carpeta (`marcadores/`) se encuentran los archivos gráficos correspondientes a cada capítulo:
- `marcador_capitulo_1.png` al `marcador_capitulo_24.png` (Versión Web / Pantalla 72 DPI, resolución $226 \times 226\text{ px}$).
- `marcador_jugador_caotico.png` (Marcador especial para el evento Caótico del Capítulo 2).
- Carpeta `impresion_300dpi/`: Todos los marcadores en alta resolución editorial (300 DPI) listos para la maqueta e impresión física en el libro impreso.

### ¿Por qué Marcadores de Código de Barras (Matrix 3x3)?
1. **Detección Instantánea y Fiabilidad:** No sufren por variaciones de iluminación o reflejos de papel como los patrones pictóricos complejos.
2. **Cero Instalación:** Funcionan directamente desde el navegador móvil con WebAR (AR.js + A-Frame) escaneando el código QR de acceso inicial.

---

## 2. Tabla Maestra de Asignación y Montaje

| Capítulo | Título Canónico | Archivo Marcador | Código Barcode | Activo 3D Montado / Placeholder |
| :--- | :--- | :--- | :--- | :--- |
| **Capítulo 1** | El Despertar / Solaris | `marcador_capitulo_1.png` | `value="1"` | `modelos/solaris_citrus.glb` (Escala 1.3, Rotación 90° horizontal) |
| **Capítulo 2** | El Código Caótico / Deltar | `marcador_capitulo_2.png` | `value="2"` | `modelos/deltar.glb` + Leyenda Neón Verde `DELTAR` |
| **Cap. 2 Extra** | Bug del Sistema / Jugador Caótico | `marcador_jugador_caotico.png` | `value="7"` | `modelos/jugador_caotico_low.glb` + Glitch `erratic-pixels` |
| **Capítulo 3** | La Cámara Oculta | `marcador_capitulo_3.png` | `value="3"` | Terminal Holográfica Dinámica (`dynamic-terminal` CRT) |
| **Capítulo 4** | El Refugio de los Niños (Rigel) | `marcador_capitulo_4.png` | `value="4"` | `modelos/open_arms.glb` + 75 píxeles vectoriales erráticos |
| **Capítulo 5** | El Mensaje en el Mercado | `marcador_capitulo_5.png` | `value="5"` | `modelos/salute_valerius.glb` (Animación saludo militar) |
| **Capítulo 6** | El Taller de los Marmoleros | `marcador_capitulo_6.png` | `value="6"` | Dodecaedro Holográfico Cian + Leyenda 3D |
| **Capítulo 7** | La Orden de la Noche | `marcador_capitulo_7.png` | `value="8"` | Octaedro Magenta Wireframe + Leyenda 3D |
| **Capítulo 8** | La Copa del Olvido | `marcador_capitulo_8.png` | `value="9"` | Cilindro Ámbar Wireframe + Leyenda 3D |
| **Capítulo 9** | El Choque en la Niebla | `marcador_capitulo_9.png` | `value="10"` | Nudo Tórix Cian Wireframe + Leyenda 3D |
| **Capítulo 10** | El Protocolo Secreto | `marcador_capitulo_10.png` | `value="11"` | Cubo Matriz Verde Neón + Leyenda 3D |
| **Capítulo 11** | El Ritual del Filo | `marcador_capitulo_11.png` | `value="12"` | Tetraedro Carmesí Wireframe + Leyenda 3D |
| **Capítulo 12** | La Nariz de Cyrano | `marcador_capitulo_12.png` | `value="13"` | Anillo Púrpura Orbital + Leyenda 3D |
| **Capítulo 13** | El Arrullo del Silencio | `marcador_capitulo_13.png` | `value="14"` | Esfera Cuántica Blanca + Leyenda 3D |
| **Cap. 14 a 24** | Expansión Saga Transmedia | `marcador_capitulo_X.png` | `value="15"` a `25` | Reservados para nuevos capítulos y módulos transmedia |

---

## 3. Instrucciones de Montaje para Nuevos Modelos 3D (.GLB)
Cuando el equipo de arte o el Director proporcione un nuevo modelo 3D optimizado:
1. Exportar obligatoriamente en formato `.glb` (GLTF binario con texturas incrustadas).
2. Guardar el archivo en `proiectio_webar/modelos/nombre_modelo.glb`.
3. En `index.html`, ubicar el `<a-marker type="barcode" value="X">` correspondiente y sustituir la figura geométrica temporal por:
   ```html
   <a-gltf-model 
     src="modelos/nombre_modelo.glb" 
     position="0 0.05 0" 
     scale="1.0 1.0 1.0" 
     rotation="0 0 0" 
     animation-mixer
     drag-rotate>
   </a-gltf-model>
   ```
