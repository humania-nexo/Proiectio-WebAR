# Documentación Oficial: Sistema de Marcadores AR para Proiectio (Capítulos 1 al 30)

Este documento detalla la arquitectura, codificación y montaje de la capa de Realidad Aumentada (WebAR) para la novela y universo transmedia *Proiectio / Cloto*.

---

## 1. Los Marcadores Físicos (Imágenes PNG)
Dentro de la carpeta `marcadores/` se encuentran todos los anclajes visuales organizados en dos resoluciones:
- **Versión Web / Pantalla (72 DPI - $226 \times 226\text{ px}$):** `marcador_capitulo_1.png` al `marcador_capitulo_35.png` y `marcador_jugador_caotico.png`.
- **Versión Editorial Impresión (300 DPI):** Subcarpeta `marcadores/impresion_300dpi/` (`marcador_capitulo_X_300dpi.png`) en alta resolución lista para maquetación física en el libro impreso.

### Características del Sistema:
1. **Doble Marcador en Capítulo 2:**
   - Marcador Estándar: Dispositivo Físico Deltar (`marcador_capitulo_2.png` ➔ Barcode `value="2"`).
   - Marcador Extra: Bug del Sistema / Jugador Caótico (`marcador_jugador_caotico.png` ➔ Barcode `value="7"`).
2. **Detección Matrix 3x3:** Códigos binarios de máxima fiabilidad y cero colisiones para móviles.

---

## 2. Tabla Maestra de Asignación y Montaje (Capítulos 1 al 30)

| Capítulo | Título Canónico | Archivo Marcador | Barcode Value | Activo 3D / Placeholder en Escena |
| :--- | :--- | :--- | :--- | :--- |
| **Capítulo 1** | *El color que se apaga / Solaris* | `marcador_capitulo_1.png` | `value="1"` | `modelos/solaris_citrus.glb` (Escala 1.3, Rotación 90° horizontal) |
| **Capítulo 2** | *El Códulo Caótico / Deltar* | `marcador_capitulo_2.png` | `value="2"` | `modelos/deltar.glb` + Leyenda Neón Verde `DELTAR` |
| **Cap. 2 (Extra)** | *Bug del Sistema / Jugador Caótico*| `marcador_jugador_caotico.png` | `value="7"` | `modelos/jugador_caotico_low.glb` + Glitch `erratic-pixels` |
| **Capítulo 3** | *La sombra del tiempo / Cámara Oculta* | `marcador_capitulo_3.png` | `value="3"` | Terminal Holográfica Dinámica (`dynamic-terminal` CRT) |
| **Capítulo 4** | *El refugio de los niños perdidos* | `marcador_capitulo_4.png` | `value="4"` | `modelos/open_arms.glb` (Rigel) + Píxeles erráticos |
| **Capítulo 5** | *Los ángeles de marfil / Valerius* | `marcador_capitulo_5.png` | `value="5"` | `modelos/salute_valerius.glb` (Animación saludo militar) |
| **Capítulo 6** | *El remix de la justicia / Marmoleros* | `marcador_capitulo_6.png` | `value="6"` | Dodecaedro Cian Holográfico + Leyenda 3D |
| **Capítulo 7** | *La cosecha de los olvidados* | `marcador_capitulo_7.png` | `value="8"` | Octaedro Magenta Wireframe + Leyenda 3D |
| **Capítulo 8** | *La copa del olvido* | `marcador_capitulo_8.png` | `value="9"` | Cilindro Ámbar Wireframe + Leyenda 3D |
| **Capítulo 9** | *El choque en la niebla* | `marcador_capitulo_9.png` | `value="10"` | Nudo Tórix Cian Wireframe + Leyenda 3D |
| **Capítulo 10** | *El protocolo secreto* | `marcador_capitulo_10.png` | `value="11"` | Cubo Matriz Verde Neón + Leyenda 3D |
| **Capítulo 11** | *El ritual del filo* | `marcador_capitulo_11.png` | `value="12"` | Tetraedro Carmesí Wireframe + Leyenda 3D |
| **Capítulo 12** | *La nariz de Cyrano* | `marcador_capitulo_12.png` | `value="13"` | Anillo Orbital Púrpura + Leyenda 3D |
| **Capítulo 13** | *El arrullo del silencio* | `marcador_capitulo_13.png` | `value="14"` | **Pantalla Holográfica de Video** (`multimedia/marta_pantalla_cap13.mp4` / `.webm`) + Haz Emisor Piramidal + Control de Audio en HUD |
| **Capítulo 14** | *El protocolo de la vergüenza* | `marcador_capitulo_14.png` | `value="15"` | Cubo Naranja Wireframe + Leyenda 3D |
| **Capítulo 15** | *El triunfo de la apatía* | `marcador_capitulo_15.png` | `value="16"` | Cilindro Gris Wireframe + Leyenda 3D |
| **Capítulo 16** | *El teatro de la luz* | `marcador_capitulo_16.png` | `value="17"` | Cono Amarillo Dorado Wireframe + Leyenda 3D |
| **Capítulo 17** | *La escuela de las sombras* | `marcador_capitulo_17.png` | `value="18"` | Dodecaedro Violeta Wireframe + Leyenda 3D |
| **Capítulo 18** | *La fe y el sindicato* | `marcador_capitulo_18.png` | `value="19"` | Octaedro Verde Esmeralda + Leyenda 3D |
| **Capítulo 19** | *La sombra de la asistente* | `marcador_capitulo_19.png` | `value="20"` | Toro Rosa Neón + Leyenda 3D |
| **Capítulo 20** | *Las rutas del espectro* | `marcador_capitulo_20.png` | `value="21"` | Nudo Tórix Cian Neón + Leyenda 3D |
| **Capítulo 21** | *El templo de la estética* | `marcador_capitulo_21.png` | `value="22"` | Anillo Dorado PBR + Leyenda 3D |
| **Capítulo 22** | *El centinela del ritmo* | `marcador_capitulo_22.png` | `value="23"` | Dodecaedro Cian Neón + Leyenda 3D |
| **Capítulo 23** | *Al margen de la luz* | `marcador_capitulo_23.png` | `value="24"` | Tetraedro Carmesí Neón + Leyenda 3D |
| **Capítulo 24** | *El derecho a la pesadilla* | `marcador_capitulo_24.png` | `value="25"` | Cubo Púrpura Sombrío + Leyenda 3D |
| **Capítulo 25** | *El banquete de los dioses* | `marcador_capitulo_25.png` | `value="26"` | Cilindro Dorado Imperial + Leyenda 3D |
| **Capítulo 26** | *La fractura del velo* | `marcador_capitulo_26.png` | `value="27"` | Esfera Turquesa Wireframe + Leyenda 3D |
| **Capítulo 27** | *El peso de la llama* | `marcador_capitulo_27.png` | `value="28"` | Cono Ígneo Naranja + Leyenda 3D |
| **Capítulo 28** | *Las cenizas de Arcadia* | `marcador_capitulo_28.png` | `value="29"` | Octaedro Plateado Wireframe + Leyenda 3D |
| **Capítulo 29** | *El despertar del Leviatán* | `marcador_capitulo_29.png` | `value="30"` | Nudo Carmesí Sangre + Leyenda 3D |
| **Capítulo 30** | *El hilo del destino* | `marcador_capitulo_30.png` | `value="31"` | Esfera Cuántica Blanca Radiante + Leyenda 3D |
| **31 al 35** | *Expansión Libro 2 (Láquesis)* | `marcador_capitulo_31..35.png`| `value="32..36"` | Marcadores de reserva pre-generados en 72 y 300 DPI |

---

## 3. Montaje de Nuevos Modelos (.GLB)
Para sustituir los placeholders geométricos por modelos 3D finales de personajes u objetos:
1. Colocar el archivo en `proiectio_webar/modelos/nombre.glb`.
2. En `index.html`, ubicar el `<a-marker type="barcode" value="X">` y cambiar la entidad geométrica por:
   ```html
   <a-gltf-model 
     src="modelos/nombre.glb" 
     position="0 0.05 0" 
     scale="1.0 1.0 1.0" 
     rotation="0 0 0" 
     animation-mixer
     drag-rotate>
   </a-gltf-model>
   ```
