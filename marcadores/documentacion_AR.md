# Documentación: Sistema de Marcadores AR para Proiectio (Capítulos 1-6)

Esta carpeta contiene todo lo necesario para ejecutar la capa de Realidad Aumentada de los primeros 6 capítulos de *Cloto*.

## 1. Los Marcadores Físicos (Imágenes PNG)
Dentro de esta carpeta (`marcadores/`) encontrarás 6 imágenes PNG numeradas (`marcador_capitulo_1.png` hasta `marcador_capitulo_6.png`).
Estos son "Marcadores de Código de Barras (Matrix 3x3)". 
- **¿Por qué usamos estos?** Porque permiten que la cámara reconozca instantáneamente qué figura 3D debe mostrar sin confundirse, y son extremadamente fiables.
- **¿Cómo se usan en el libro?** Cada uno de estos cuadrados negros con recuadros blancos debe ir impreso en la página correspondiente de cada capítulo.

## 2. El Código Base (Cómo funciona)
El código HTML que está en la carpeta principal (`index.html`) utiliza la biblioteca **AR.js** configurada en modo `matrixCodeType: 3x3`. 

Esto significa que el código "escucha" y busca códigos de barras del 1 al 6. Cuando encuentra el marcador `value="1"`, despliega el contenido 3D que tenga asignado.

### Copia de seguridad del código de los marcadores:
```html
<!-- Escena configurada para detectar Códigos de Barras -->
<a-scene embedded arjs="sourceType: webcam; debugUIEnabled: false; detectionMode: mono_and_matrix; matrixCodeType: 3x3;">
  
  <!-- Marcador para el Capítulo 1 -->
  <a-marker type="barcode" value="1">
    <!-- Aquí irá el modelo .glb de Elías Vance. Por ahora hay un cubo rojo -->
    <a-box position="0 0.5 0" color="#FF0000"></a-box>
    <a-text value="CAPITULO 1" position="-0.5 1.5 0"></a-text>
  </a-marker>

  <!-- Marcador para el Capítulo 2 -->
  <a-marker type="barcode" value="2">
    <!-- Aquí irá el segundo modelo. Por ahora hay una esfera azul -->
    <a-sphere position="0 0.5 0" radius="0.5" color="#0000FF"></a-sphere>
    <a-text value="CAPITULO 2" position="-0.5 1.5 0"></a-text>
  </a-marker>

  <!-- (Y así sucesivamente hasta el marcador value="6") -->

  <a-entity camera></a-entity>
</a-scene>
```

## 3. Próximos Pasos (Cuando tengas los modelos de Meshy AI)
Cuando obtengas tus modelos `.glb` desde la Inteligencia Artificial (ej. Meshy AI o Tripo3D):
1. Guarda el archivo `modelo.glb` en la carpeta de tu web.
2. Abre el `index.html`.
3. Busca la línea del marcador correspondiente (ej. `<a-marker type="barcode" value="1">`).
4. Borra el cubo (`<a-box...>`) y reemplázalo por tu modelo así:
   `<a-gltf-model src="tu_modelo_elias.glb" position="0 0 0" scale="0.5 0.5 0.5"></a-gltf-model>`
