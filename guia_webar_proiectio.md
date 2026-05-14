# Pipeline de Realidad Aumentada: Proyecto CLOTO

Este documento detalla la arquitectura y el flujo de trabajo tecnológico para dar vida a los personajes de *Cloto* (Elías Vance, Rigel, Los Templarios) mediante Realidad Aumentada (WebAR) sin necesidad de que el usuario descargue aplicaciones.

## 1. La Arquitectura de Inmersión ("Ojos del Alma")

Para mantener una lectura ininterrumpida y altamente inmersiva, se utilizará el enfoque de **Marcadores Múltiples**:

1. **El Portal (QR de Portada):** Al inicio del libro físico, habrá un único Código QR. Este código abrirá la página web alojada en los servidores de *Humania / Sofi Mind*, solicitará acceso a la cámara y cargará en segundo plano todos los modelos 3D ligeros.
2. **Los Anclajes Físicos (Marcadores en páginas):** A lo largo del libro, se imprimirán diferentes marcadores de reconocimiento (Patrones o Códigos de Barras). 
3. **El Efecto:** Con la cámara abierta, el lector solo debe pasar las páginas. Al detectar el Marcador "A", aparecerá Elías Vance. Al pasar de página y detectar el Marcador "B", el sistema automáticamente ocultará a Vance y proyectará a Rigel.

---

## 2. El Flujo de Creación 3D (Presupuesto Cero)

Para crear los personajes e introducirlos en la web, el orden inquebrantable de trabajo es el siguiente:

1. **Modelado y Texturizado (Blender):** Diseño del personaje. Usar generadores base (MB-Lab) para la anatomía humana y Blender para el atuendo (armaduras, ceniza, túnicas).
2. **Animación Automática (Mixamo):** Exportar el modelo base y subirlo a Mixamo.com (de Adobe). Aplicar el Auto-Rigger y descargar animaciones realistas de "respiración/espera" (Idle).
3. **Exportación Obligatoria a formato `.GLB`:**
   > [!IMPORTANT]  
   > **NUNCA exportar en `.OBJ`, `.FBX` o `.GLTF` con archivos separados.** La web móvil requiere estrictamente el formato `.glb` (GLTF Binario). Este formato empaqueta el esqueleto, la animación y las texturas en un solo archivo hermético, previniendo errores de seguridad (CORS) y garantizando una carga rápida.

---

## 3. Plantilla de Código Base (AR.js)

Cuando los modelos `.glb` estén listos, este es el código HTML maestro que funciona como motor de Realidad Aumentada:

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, user-scalable=no, minimum-scale=1.0, maximum-scale=1.0">
  <!-- Importación de A-Frame y AR.js -->
  <script src="https://aframe.io/releases/1.3.0/aframe.min.js"></script>
  <script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
</head>
<body style="margin : 0px; overflow: hidden;">
  <!-- Escena AR optimizada para móviles -->
  <a-scene embedded arjs="sourceType: webcam; debugUIEnabled: false;">
    
    <!-- 1. CARGA DE MODELOS EN SEGUNDO PLANO -->
    <a-assets>
      <a-asset-item id="modeloVance" src="./modelos/elias_vance.glb"></a-asset-item>
      <a-asset-item id="modeloRigel" src="./modelos/rigel.glb"></a-asset-item>
    </a-assets>

    <!-- 2. MARCADOR DE VANCE (Ejemplo: Capítulo 1) -->
    <!-- 'preset="hiro"' o un patrón entrenado personalizado -->
    <a-marker preset="hiro">
      <!-- El modelo se proyecta con una animación cíclica -->
      <a-gltf-model position="0 0 0" scale="0.05 0.05 0.05" src="#modeloVance" 
                    animation-mixer="loop: repeat"></a-gltf-model>
    </a-marker>

    <!-- 3. MARCADOR DE RIGEL (Ejemplo: Capítulo 5) -->
    <a-marker preset="kanji">
      <a-gltf-model position="0 0 0" scale="0.05 0.05 0.05" src="#modeloRigel" 
                    animation-mixer="loop: repeat"></a-gltf-model>
    </a-marker>
    
    <!-- Cámara Virtual -->
    <a-entity camera></a-entity>
  </a-scene>
</body>
</html>
```

---

## 4. Próximos Pasos Técnicos para el Futuro

Cuando retomes esta etapa del proyecto, los pasos a seguir serán:

1. **Diseñar los Marcadores Propios:** Usaremos una herramienta llamada *AR.js Marker Training* para transformar logos simplificados de *Proiectio* en archivos de patrón (`.patt`). Así no usaremos marcadores genéricos (Hiro/Kanji), sino sellos estéticos relacionados con *Sofi Mind* y la deidad *Cloto*.
2. **Optimización de Polígonos:** Asegurarse de que los modelos de Blender no superen los 20,000 polígonos por personaje, para evitar que los celulares antiguos se sobrecalienten.
3. **Publicación Web:** Subir este código a un servidor con certificación HTTPS (ej. GitHub Pages, Vercel o el propio hosting corporativo ficticio de Humania) para que la cámara del celular conceda permisos de acceso.
