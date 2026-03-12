================================================================================
  SUPERCALC — README
  Super Calculator | Álgebra Lineal + Física + Cálculo
  github.com/xii1rst/Graph-Vector
================================================================================


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  HISTORIAL DE CAMBIOS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

v1.0.0  > Se creó el programa base para visualizar vectores en R³ con canvas 2D.
          Rotación 3D con proyección isométrica, paleta de colores fija (PAL),
          panel inferior con tabs: Vectores, Magnitud, Operaciones, Ecuaciones,
          Incógnitas.

v1.1.0  > Sistema de versionado n.n.n. Se añadió etiqueta de versión visible
          bajo el logo. Etiquetas de nombre de vector en la punta de la flecha.
          Punto de origen más grande. Zoom con rueda del ratón. Advertencia
          |v|=0 cuando la magnitud del vector es cero. Secciones colapsables
          en el tab Cálculos. Vista previa de expresiones en tiempo real en
          Operaciones.

v1.1.1  > Service Worker (SW) inline + manifest PWA sin archivos externos.
          Compatible con GitHub Pages. Banner de actualización (verde, arriba)
          y banner de instalación (dorado, abajo).

v1.2.0  > Proyecciones ortogonales en R²: líneas punteadas desde la punta del
          vector hasta los ejes X e Y, con puntos en los pies de cada proyección.
          Mismo estilo que las proyecciones en R³ (opacidad 32%, 1.5px, dash 4-4).

v1.3.0  > Subdivisiones de cuadrícula: puntos principales cada 2u (1.9px) y
          puntos secundarios cada 1u (0.85px) con fundido radial. Aplicado
          tanto en R² como en R³.

v1.4.0  > Cubo volumétrico 3D de puntos en R³: cubo completo ±10u, puntos
          principales en coordenadas pares, secundarios en impares, alpha
          con desvanecimiento radial desde el origen.

v1.5.0  > Interruptor de panel (toggle switch) encima del panel inferior,
          alineado a la derecha. Ticks adaptativos en ejes: 2u (0-20),
          5u (21-49), 10u (50+). SW inline + manifest actualizados para
          GitHub Pages.

v1.6.0  > Switch DEC/FRAC en el header: alterna entre notación decimal y
          fracciones exactas (p/q) en todos los resultados del panel AL.
          Función toFrac() con algoritmo de fracciones continuas. Switch FIG
          para mostrar/ocultar figura geométrica auxiliar en el canvas
          (pirámide, cubo, esfera según modo).

v1.7.0  > Modo R² completo: botón R²/R³ en header para alternar entre plano
          y espacio. En R² se oculta la componente Z en las tarjetas de
          vectores y se usa proyección 2D directa. Operaciones y ecuaciones
          adaptadas al modo activo.

v1.8.0  > Rediseño del header del módulo AL: los controles DEC/FRAC, FIG y
          R²/R³ reorganizados en una fila compacta a la derecha. Estilos
          unificados para los tres controles (mismo tamaño, misma tipografía,
          mismo comportamiento visual del switch).

v2.0.0  > REESCRITURA MAYOR. Pantalla de lanzamiento con dos módulos:
          Álgebra Lineal (AL, dorado) y ElectroMag (EM, azul).
          El módulo AL contiene la app de vectores existente.
          El módulo EM es nuevo, con 6 tabs universitarios:
            · Coulomb:   F = k·q₁·q₂/r²
            · Gauss:     Φ = Q_enc/ε₀
            · Potencial: V = k·Q/r, ΔV, W = q·ΔV
            · Lorentz:   F = q(E + v×B)
            · Faraday:   ε = −N·dΦ/dt
            · Maxwell:   4 ecuaciones + velocidad de la luz + vector Poynting
          Sistema de coordenadas: XYZ / CIL (cilíndricas) / ESF (esféricas).
          Interruptor de panel también en EM (acento azul).
          Canvas EM con fondo oscuro y ejes básicos.

v2.1.0  > Paridad visual EM ↔ AL. El canvas de EM adopta el mismo estilo que AL:
          cubo volumétrico de puntos (±10u), ticks adaptativos con etiquetas,
          punto de origen con glow, ejes con grosor/dash idénticos al AL,
          etiquetas de vectores en la punta. Botón ↺ Reset en canvas EM.

v2.1.1  > Corrección: el canvas de EM se iniciaba descentrado al abrir el módulo
          por primera vez. Se agregó doble resize escalonado post-transición.

v2.1.2  > Optimización de rendimiento del canvas EM:
          · Cubo reducido de ±10 a ±8 unidades (−46% de puntos)
          · Depth sorting: puntos ordenados de atrás hacia adelante
          · Throttling con requestAnimationFrame durante drag/pinch

v2.1.3  > Se eliminó el cubo volumétrico del canvas EM. Se mantienen únicamente
          puntos de referencia sobre el eje X.

v2.1.4  > Corrección zoom EM: el pinch-to-zoom afectaba la página completa.
          Se añadió touch-action:none al canvas y su contenedor, y
          e.preventDefault() en el touchmove con passive:false.

v2.1.5  > Paridad de ejes EM ↔ AL: los ejes del módulo EM ahora reutilizan
          exactamente las mismas funciones drawAxis3 y drawAxisTicks3 del AL,
          usando emCtx como contexto. Mismo grosor (2.5px), mismo glow, misma
          tipografía y mismos negativos punteados.

v2.1.6  > Corrección crítica: template literal sin cerrar en emCalcMaxwell
          rompía todo el JavaScript. Corregido. Se eliminaron todos los símbolos
          Unicode dentro de strings JS que causaban cuadros (□) en algunos
          dispositivos.

v2.1.7  > Todas las fórmulas matemáticas del módulo EM reescritas con entidades
          HTML estándar (&nabla;, &epsilon;, &mu;, &part;, &Phi;, <sub>, <sup>)
          para garantizar renderizado correcto en todos los navegadores.

v2.1.8  > Las flechas vectoriales ⃗ (&#8407;) reemplazadas por negrita HTML
          (<b>F</b>, <b>E</b>, etc.) ya que Space Mono no soporta ese carácter.

v2.1.9  > Corrección: script duplicado completo (todas las funciones declaradas
          dos veces) que causaba pantalla en blanco. Se fusionaron y depuraron
          los dos bloques <script> en uno solo sin duplicados.

v3.0.0  > REESCRITURA ARQUITECTURAL. Nombre cambia a "SuperCalc".
          Nueva pantalla de inicio con logo ∑ y dos módulos principales:
            · Álgebra Lineal (AL) — violeta
            · Física (FÍS) — cyan
          Cada módulo tiene un submenú propio.
          AL ahora tiene 3 secciones:
            · Vectores 3D (app original)
            · Matrices & Ecuaciones Lineales:
                - Operaciones entre N matrices de tamaño m×n variable
                  (suma, resta, producto encadenado, escalar, transpuesta)
                - Determinante e inversa (Gauss-Jordan)
                - Sistemas de ecuaciones (Gauss-Jordan con pasos / Cramer)
                - Valores y vectores propios (iteración potencia)
            · Inecuaciones:
                - Lineal (ax + b ⋛ c)
                - Cuadrática (ax² + bx + c ⋛ 0)
                - Sistema (dos inecuaciones lineales)
                - Valor absoluto (|ax + b| ⋛ c)
                - Recta numérica visual por tipo
          Física mantiene Electromagnetismo + slot para secciones futuras.
          Vectores: empieza vacío (sin vectores por defecto), canvas carga
          correctamente al abrir, UI rediseñada con paleta unificada (violeta).
          Manifest PWA actualizado: nombre "SuperCalc", ícono ∑ generado
          dinámicamente con canvas, theme_color violeta.
          Separación de archivos: index.html + style.css + app.js.

v4.0.0  > NUEVO MÓDULO: Cálculo. Tercer módulo principal (color esmeralda).
          4 submódulos con teclado de símbolos tipo C (agrupado por categoría):

          · Cálculo Diferencial:
              - Límites: bilateral, lateral derecho/izquierdo, en el infinito
              - Derivadas: 1ra, 2da y 3ra orden; simbólica + numérica (Richardson)
              - Evaluación en un punto
              - Análisis completo: puntos críticos, máx/mín locales, concavidad

          · Cálculo Integral:
              - Integral indefinida: reglas simbólicas (potencia, sin, cos, ln, eˣ,
                tan, arcsin, arccos, arctan, integración por partes básica)
              - Integral definida: método de Simpson 1/3 (n=1000)
              - Serie de Taylor/Maclaurin: N términos, centro a configurable

          · Cálculo Multivariable:
              - Derivadas parciales ∂f/∂x, ∂f/∂y, 1er y 2do orden
              - Gradiente ∇f: magnitud, dirección, versor unitario
              - Integral doble ∬: Simpson 2D (50×50), Teorema de Fubini

          · Ecuaciones Diferenciales:
              - ED 1er orden variables separables (RK4)
              - ED lineal 1er orden y'+P(x)y=Q(x) (factor integrante + RK4)
              - ED 2do orden coef. constantes ay''+by'+cy=0:
                raíces reales distintas, raíz doble, raíces complejas

          Módulo AL Vectores — nuevas funcionalidades:
            · Tab "Triángulo 3D": ingreso de 3 puntos P/Q/R, cálculo de lados
              (con notación √n), ángulos (formato D°MM'SS"), perímetro, área,
              verificación de suma de ángulos, pasos detallados, visualización
              en canvas con backup/restore de vectores previos.
            · Tab "Cálculos" — tarjetas expandibles con pasos completos:
                - Producto punto: multiplicación por componentes + suma
                - Ángulo: cadena cos⁻¹ con |A|, |B|, cos θ
                - Proyecciones: fórmula + sustitución
                - Producto cruz: determinante 3×3 con filas i/j/k + magnitud
            · Notación √n para magnitudes exactas (fMag): si x² es entero
              devuelve √n sin simplificar; si es entero exacto, lo muestra entero.
            · Formato D°MM'SS" para ángulos (fDMS): ángulos director αx/αy/αz
              y todos los ángulos entre vectores.
            · fN recorta ceros finales: "16.0000" → "16", "3.14" → "3.14".
            · uV() llama a rLeg() en tiempo real al escribir coordenadas.
            · launchSubmod('ineq') corregido (caso faltante).

          Módulo AL — layout responsive de escritorio (≥700px):
            · #app-body usa flex-direction:row — canvas izquierda, panel derecha
              (380px / 440px / 520px en breakpoints 700 / 1000 / 1400px).
            · togglePanel() retorna early en escritorio.
            · #panel-tog-wrap oculto en escritorio.
            · Todos los paneles de módulos usan max-height:none y overflow-y:auto
              en escritorio (AL, FÍS, MAT, INEQ, CAL).
            · Header flex-wrap:nowrap para mantener controles en una sola fila.

          Service Worker actualizado: cache key 'supercalc-4.0.0',
          Promise.allSettled en install, estrategia cache-first en fetch.
          Separación de archivos mantenida: index.html + style.css + app.js.

v4.1.0  > VISUAL & IDENTIDAD. Rediseño del logo y fondo de la aplicación.

          · Logo rediseñado — Ω como núcleo atómico:
              - Símbolo Ω (Georgia serif, gradiente lavanda → violeta profundo)
                con efecto de flotación suave (translateY, 3.6s ease-in-out).
              - 3 órbitas elípticas en planos distintos (0°, 60°, −60°),
                trazadas con stroke-dasharray para aspecto orbital.
              - 3 electrones animados por requestAnimationFrame:
                  · ∑ (violeta) — órbita horizontal
                  · π (cian, font-size reducido 30% para diferenciar del Ω)
                  · ∂ (dorado) — órbita inclinada −60°
              - Grid cartesiano de fondo dentro del SVG (sin ejes X/Y,
                solo la cuadrícula de líneas finas en violeta tenue).
              - Halo radial de glow alrededor del núcleo.
              - Procesador y ejes eliminados del diseño final.

          · Background de fórmulas matemáticas y físicas:
              - Canvas fijo (#sc-bg-canvas, z-index:0) debajo de toda la UI.
              - ~60 fórmulas y símbolos: E=mc², F=ma, ∇·E=ρ/ε₀, eⁱᵖ+1=0,
                letras griegas (α β γ θ λ μ ν ρ σ τ φ ψ ω), operadores
                (∫ ∂ ∇ ∑ Π √ ± ≈ ∈ ∅ ħ Δ ∮), fórmulas de física y análisis.
              - Dispersión estilo WhatsApp: posición, tamaño (9–20px),
                rotación (±0.25 rad) y opacidad (4.5–13.5%) aleatorios.
              - Anti-solapamiento por bounding box rotado + padding 6px:
                  · Mide cada texto con canvas offscreen (measureText)
                  · Calcula AABB conservador considerando el ángulo
                  · Hasta 20 intentos por item; omite si no encuentra espacio
                  · Lista placed[] acumula zonas ocupadas en O(n²)
              - Regeneración aleatoria en cada carga y en cada resize
                (debounce 120ms para no redibujar en cascada).
              - Loop permanente con requestAnimationFrame + flag needsRedraw
                para garantizar presencia constante del fondo.
              - Todo el contenido de la UI elevado a z-index:1 con
                backdrop-filter:blur en tarjetas y píldoras de módulo.

          · Service Worker: cache key actualizado a 'supercalc-4.1.0'.


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  GLOSARIO DE ABREVIATURAS
  Formato:  Abreviatura  --->  Significado completo  !  Tipo
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  VARIABLES
  ─────────────────────────────────────────────────────────────────────────────

  EM_EPS0         --->  ElectroMag Epsilon Zero (ε₀ = 8.854×10⁻¹² F/m)        ! Variable constante
  EM_K            --->  ElectroMag Konstante Coulomb (k = 8.9875×10⁹ N·m²/C²) ! Variable constante
  EM_MU0          --->  ElectroMag Mu Zero (μ₀ = 4π×10⁻⁷ N/A²)                ! Variable constante
  PAL             --->  PALeta de colores (array hex para vectores AL)          ! Variable constante
  RC              --->  Result Color (color de resultados, violeta)             ! Variable constante
  SUBMOD_CONFIG   --->  SUBMODule CONFIGuration (definición de submenús)       ! Variable constante
  currentParent   --->  current Parent module (módulo padre activo: al/fi/ca)  ! Variable de estado
  cv              --->  CanVas (referencia al canvas principal de AL)           ! Variable de referencia
  deferredPrompt  --->  deferred Prompt (evento PWA install diferido)          ! Variable de estado
  emCanvas        --->  ElectroMag Canvas (referencia al canvas del módulo EM) ! Variable de referencia
  emCoord         --->  ElectroMag COORDinate system (cart / cyl / sph)        ! Variable de estado
  emInitDone      --->  ElectroMag INITialization Done (bandera de inicio)     ! Variable de estado
  emObjects       --->  ElectroMag Objects (array de objetos a dibujar en EM)  ! Variable de estado
  emResult        --->  ElectroMag Result (último resultado calculado en EM)   ! Variable de estado
  emScl           --->  ElectroMag SCaLe (zoom actual del canvas EM)           ! Variable de estado
  ineqType        --->  INEQuality Type (tipo de inecuación activa)            ! Variable de estado
  matCurrentTab   --->  MATrix Current Tab (tab activo en módulo matrices)     ! Variable de estado
  matOpsState     --->  MATrix OPerations State (estado completo operaciones)  ! Variable de estado
  mode            --->  mode (modo de visualización: 2=R², 3=R³)               ! Variable de estado
  needsRedraw     --->  NEEDS REDRAW (flag para redibujo del bg canvas)        ! Variable de estado
  nid             --->  Next ID (contador para ID único de vectores)           ! Variable de estado
  opI             --->  OPeration Indices (índices de vectores en operación)   ! Variable de estado
  opS             --->  OPeration Symbol (símbolo de operación: +/-/×/·)       ! Variable de estado
  palIdx          --->  PALette InDeX (índice actual de color en PAL)          ! Variable de estado
  rotX            --->  ROTation X (ángulo de rotación vertical del canvas AL) ! Variable de estado
  sisFracMode     --->  SIStem FRACtion MODE (modo fraccionario en matrices)   ! Variable de estado
  toRad           --->  TO RADians (función conversión grados→radianes)        ! Variable/lambda
  unkOp           --->  UNKnown OPeration (operación en tab de incógnitas)     ! Variable de estado
  unkVecs         --->  UNKnown VECtorS (vectores definidos en tab incógnitas) ! Variable de estado
  vangle          --->  Vector ANGLE (lambda: ángulo entre dos vectores)       ! Variable/lambda
  vcross          --->  Vector CROSS product (lambda: producto vectorial)      ! Variable/lambda
  vdot            --->  Vector DOT product (lambda: producto punto)            ! Variable/lambda
  vecs            --->  VECtorS (array principal de vectores en AL)            ! Variable de estado
  vmag            --->  Vector MAGnitude (lambda: magnitud de un vector)       ! Variable/lambda
  vproj           --->  Vector PROJection (lambda: proyección de a sobre b)    ! Variable/lambda


  FUNCIONES
  ─────────────────────────────────────────────────────────────────────────────

  adaptiveStep    --->  ADAPTIVE STEP (calcula paso de ticks según zoom)       ! Función utilitaria
  addUnkVec       --->  ADD UNKnown VECtor (agrega vector al tab incógnitas)   ! Función UI
  addV            --->  ADD Vector (agrega nuevo vector a la lista AL)         ! Función UI
  angSteps        --->  ANGle STEPS (genera HTML pasos del cálculo de ángulo)  ! Función UI
  buildIneqForm   --->  BUILD INEQuality FORM (construye formulario por tipo)  ! Función UI
  calcInit        --->  CALCulus INITialize (inicializa módulo Cálculo)        ! Función init
  calcTab         --->  CALCulus TAB (cambia tab activo en módulo Cálculo)     ! Función UI
  checkIneq       --->  CHECK INEQuality (evalúa si a ⊳ b con símbolo dado)   ! Función utilitaria
  closeModule     --->  CLOSE MODULE (cierra módulo activo, regresa submenú)   ! Función navegación
  closeSubmod     --->  CLOSE SUBMODule (cierra submenú, regresa launcher)     ! Función navegación
  compute         --->  COMPUTE (calcula operación vectorial seleccionada)     ! Función cálculo
  delUnkVec       --->  DELete UNKnown VECtor (elimina vector de incógnitas)   ! Función UI
  delV            --->  DELete Vector (elimina vector por ID)                  ! Función UI
  draw            --->  DRAW (renderiza frame completo del canvas AL)          ! Función render
  drawArrow       --->  DRAW ARROW (dibuja flecha 2D con punta triangular)     ! Función render
  drawAxis3       --->  DRAW AXIS 3d (dibuja un eje con label y negativos)     ! Función render
  drawAxisTicks2  --->  DRAW AXIS TICKS 2d (ticks sobre eje en R²)             ! Función render
  drawAxisTicks3  --->  DRAW AXIS TICKS 3d (ticks sobre eje en R³)             ! Función render
  drawNumLine     --->  DRAW NUMber LINE (dibuja recta numérica canvas)        ! Función render
  eduHint         --->  EDUcational HINT (muestra pista educativa en panel)    ! Función UI
  emCalcCoulomb   --->  EM CALCulate COULOMB (calcula Ley de Coulomb)          ! Función cálculo
  emCalcFaraday   --->  EM CALCulate FARADAY (calcula FEM inducida)            ! Función cálculo
  emCalcGauss     --->  EM CALCulate GAUSS (calcula flujo y campo Gauss)       ! Función cálculo
  emCalcLorentz   --->  EM CALCulate LORENTZ (calcula fuerza de Lorentz)       ! Función cálculo
  emCalcMaxwell   --->  EM CALCulate MAXWELL (calcula onda EM en el vacío)     ! Función cálculo
  emCalcPotential --->  EM CALCulate POTENTIAL (calcula V, ΔV, trabajo)        ! Función cálculo
  emDraw          --->  EM DRAW (renderiza frame completo del canvas EM)       ! Función render
  emDrawArrow     --->  EM DRAW ARROW (dibuja flecha en canvas EM)             ! Función render
  emFmt           --->  EM ForMaT number (formatea número científico EM)       ! Función utilitaria
  emInit          --->  EM INITialize (inicializa módulo EM al abrirlo)        ! Función init
  emP3            --->  EM Project 3d (proyecta punto 3D a coordenadas 2D)     ! Función matemática
  emRenderAllPanels --> EM RENDER ALL PANELS (llama a todos los render EM)     ! Función UI
  emRenderCoulomb --->  EM RENDER COULOMB (genera HTML del panel Coulomb)      ! Función UI
  emRenderFaraday --->  EM RENDER FARADAY (genera HTML del panel Faraday)      ! Función UI
  emRenderGauss   --->  EM RENDER GAUSS (genera HTML del panel Gauss)          ! Función UI
  emRenderLorentz --->  EM RENDER LORENTZ (genera HTML del panel Lorentz)      ! Función UI
  emRenderMaxwell --->  EM RENDER MAXWELL (genera HTML del panel Maxwell)      ! Función UI
  emRenderPotential --> EM RENDER POTENTIAL (genera HTML del panel Potencial)  ! Función UI
  emResetView     --->  EM RESET VIEW (restaura rotación/zoom del canvas EM)   ! Función UI
  emResizeCanvas  --->  EM RESIZE CANVAS (ajusta canvas EM al contenedor)      ! Función render
  emSetCoord      --->  EM SET COORDinate (cambia sistema: cart/cyl/sph)       ! Función UI
  emShowTab       --->  EM SHOW TAB (muestra panel de tab seleccionado en EM)  ! Función UI
  emToCart        --->  EM TO CARTesian (convierte coordenadas a cartesianas)  ! Función matemática
  emTogglePanel   --->  EM TOGGLE PANEL (muestra/oculta panel inferior EM)     ! Función UI
  fDMS            --->  Format Degrees Minutes Seconds (decimal → D°MM'SS")   ! Función utilitaria
  fMag            --->  Format MAGnitude (entero / √n / decimal según caso)    ! Función utilitaria
  fN              --->  Format Number (decimal recortando ceros finales)       ! Función utilitaria
  fV              --->  Format Vector (formatea vector como string)            ! Función utilitaria
  flipSym         --->  FLIP SYMbol (invierte símbolo de desigualdad: >→<)    ! Función utilitaria
  gcd             --->  Greatest Common Divisor (máximo común divisor)        ! Función matemática
  goHome          --->  GO HOME (alias legado: cierra EM, regresa submenú)    ! Función navegación
  initVectorsApp  --->  INIT VECTORS APP (inicializa módulo vectores AL)      ! Función init
  ineqBack        --->  INEQuality BACK (regresa al selector de tipo)         ! Función navegación
  ineqIntersect   --->  INEQuality INTERSECT (intersección de dos intervalos)  ! Función matemática
  ineqIntervalLinear -> INEQuality INTERVAL LINEAR (intervalo solución lineal) ! Función matemática
  ineqLinearBound --->  INEQuality LINEAR BOUND (límite inecuación lineal)     ! Función matemática
  ineqSetType     --->  INEQuality SET TYPE (activa tipo y construye solver)   ! Función UI
  ineqShowResult  --->  INEQuality SHOW RESULT (renderiza resultado+pasos)     ! Función UI
  ineqSolveAbs    --->  INEQuality SOLVE ABSolute (resuelve |ax+b|⊳c)         ! Función cálculo
  ineqSolveLinear --->  INEQuality SOLVE LINEAR (resuelve ax+b⊳c)             ! Función cálculo
  ineqSolveQuad   --->  INEQuality SOLVE QUADratic (resuelve ax²+bx+c⊳0)     ! Función cálculo
  ineqSolveSystem --->  INEQuality SOLVE SYSTEM (resuelve sistema 2 ineqs)    ! Función cálculo
  ineqSymCycle    --->  INEQuality SYMbol CYCLE (cicla entre <, ≤, >, ≥)     ! Función UI
  launchSubmod    --->  LAUNCH SUBMODule (abre módulo: vectors/em/mat/ineq/calc)! Función navegación
  matAdd          --->  MATrix ADD (suma/resta dos matrices)                   ! Función matemática
  matBuildDet     --->  MATrix BUILD DETerminant (construye grid det/inv)     ! Función UI
  matBuildEig     --->  MATrix BUILD EIGenvalue (construye grid eigenvalores)  ! Función UI
  matBuildGrids   --->  MATrix BUILD GRIDS (alias compatibilidad ops)         ! Función UI
  matBuildSis     --->  MATrix BUILD SIStem (construye grid sistemas)         ! Función UI
  matCalcDet      --->  MATrix CALCulate DETerminant (calcula determinante)   ! Función cálculo
  matCalcEig      --->  MATrix CALCulate EIGenvalues (calcula eigenvalores)   ! Función cálculo
  matCalcInv      --->  MATrix CALCulate INVerse (calcula inversa)            ! Función cálculo
  matCalcOps      --->  MATrix CALCulate OPerationS (ejecuta op. matricial)   ! Función cálculo
  matCalcSis      --->  MATrix CALCulate SIStem (resuelve sistema lineal)     ! Función cálculo
  matClearDet     --->  MATrix CLEAR DETerminant (limpia panel det/inv)       ! Función UI
  matClearEig     --->  MATrix CLEAR EIGenvalue (limpia panel eigen)          ! Función UI
  matClearOps     --->  MATrix CLEAR OPerationS (resetea operaciones)         ! Función UI
  matClearSis     --->  MATrix CLEAR SIStem (limpia panel sistemas)           ! Función UI
  matCramer       --->  MATrix CRAMER (resuelve sistema por regla de Cramer)  ! Función matemática
  matDeflate      --->  MATrix DEFLATE (deflación tras extraer eigenvalor)    ! Función matemática
  matDet          --->  MATrix DETerminant (calcula det por cofactores)       ! Función matemática
  matEigenAll     --->  MATrix EIGEN ALL (calcula todos los eigenvalores)     ! Función matemática
  matFmtMatrix    --->  MATrix ForMaT MATRIX (formatea matriz como HTML)      ! Función utilitaria
  matFmtNum       --->  MATrix ForMaT NUMber (redondea número a d decimales)  ! Función utilitaria
  matGauss        --->  MATrix GAUSS (eliminación Gauss-Jordan con pasos)     ! Función matemática
  matGetGrid      --->  MATrix GET GRID (lee valores de inputs en grid)       ! Función utilitaria
  matInit         --->  MATrix INITialize (inicializa todos los panels)       ! Función init
  matInv          --->  MATrix INVerse (calcula inversa por Gauss-Jordan)     ! Función matemática
  matMakeGrid     --->  MATrix MAKE GRID (genera HTML de grid de inputs)      ! Función UI
  matMul          --->  MATrix MULtiply (multiplica dos matrices)             ! Función matemática
  matOpsAddMatrix --->  MATrix OPS ADD MATRIX (agrega matrix a operaciones)   ! Función UI
  matOpsGetMatrix --->  MATrix OPS GET MATRIX (lee una matriz del estado)     ! Función utilitaria
  matOpsRebuild   --->  MATrix OPS REBUILD (reconstruye UI al cambiar op)     ! Función UI
  matOpsRemoveMatrix -> MATrix OPS REMOVE MATRIX (elimina última matriz)      ! Función UI
  matOpsRenderControls-> MATrix OPS RENDER CONTROLS (controles + botones)    ! Función UI
  matOpsRenderGrids --> MATrix OPS RENDER GRIDS (renderiza grids de inputs)   ! Función UI
  matOpsReset     --->  MATrix OPS RESET (reinicia estado de operaciones)     ! Función UI
  matOpsSizeChange --->  MATrix OPS SIZE CHANGE (cambia dims de una matriz)   ! Función UI
  matPowerIter    --->  MATrix POWER ITERation (iteración potencia eigenval)   ! Función matemática
  matScale        --->  MATrix SCALE (multiplica matriz por escalar)           ! Función matemática
  matTab          --->  MATrix TAB (cambia tab activo en módulo matrices)     ! Función UI
  matTranspose    --->  MATrix TRANSPOSE (transpone una matriz)               ! Función matemática
  mathTogSteps    --->  MATH TOGgle STEPS (expande/colapsa pasos en math-card)! Función UI
  mkCard          --->  MaKe CARD (genera HTML de math-card con steps toggle) ! Función UI
  openAllSections --->  OPEN ALL SECTIONS (expande todos los acordeones)      ! Función UI
  openSubmod      --->  OPEN SUBMODule (abre pantalla de submenú del módulo)  ! Función navegación
  p2              --->  Project 2d (proyecta punto 2D con escala y offset)    ! Función matemática
  p3              --->  Project 3d (proyecta punto 3D con rotación a 2D)      ! Función matemática
  parseComp       --->  PARSE COMPonent (parsea componente de expresión)      ! Función utilitaria
  pLin            --->  Print LINear (renderiza resultado ecuación lineal)     ! Función UI
  rE              --->  Render Equation (renderiza panel de ecuaciones)        ! Función UI
  rI              --->  Render Incognitas (renderiza panel de incógnitas)      ! Función UI
  rLeg            --->  Render LEGend (actualiza leyenda lateral del canvas)   ! Función UI
  rM              --->  Render Magnitud (renderiza panel de magnitudes)        ! Función UI
  rO              --->  Render Operaciones (renderiza panel de operaciones)    ! Función UI
  renderVecs      --->  RENDER VECtorS (genera HTML de tarjetas de vectores)   ! Función UI
  resetView       --->  RESET VIEW (restaura rotación y zoom del canvas AL)   ! Función UI
  resize          --->  RESIZE (ajusta canvas AL al tamaño del contenedor)    ! Función render
  runSolve        --->  RUN SOLVE (ejecuta resolución de ecuación)            ! Función cálculo
  runUnkSolve     --->  RUN UNKnown SOLVE (resuelve sistema de incógnitas)    ! Función cálculo
  saveR           --->  SAVE Result (guarda resultado en historial)           ! Función utilitaria
  saveSol         --->  SAVE SOLution (guarda solución de ecuación)           ! Función utilitaria
  setMode         --->  SET MODE (cambia entre R² y R³)                       ! Función UI
  setUnkOp        --->  SET UNKnown OPeration (define operación incógnitas)   ! Función UI
  showInstallBanner ->  SHOW INSTALL BANNER (muestra banner PWA instalación)   ! Función UI
  showTab         --->  SHOW TAB (muestra tab: V/M/O/E/I/T en panel AL)       ! Función UI
  showUpdateBanner --->  SHOW UPDATE BANNER (muestra banner de actualización) ! Función UI
  sO              --->  Save Operaciones (guarda resultado de operación)       ! Función utilitaria
  solveEq         --->  SOLVE EQuation (resuelve ecuación lineal/cuadrática)  ! Función cálculo
  tO              --->  Toggle Operaciones (alterna visibilidad de resultado)  ! Función UI
  toFrac          --->  TO FRACtion (convierte decimal a fracción p/q)        ! Función utilitaria
  togV            --->  TOGgle Vector (activa/desactiva un vector por ID)     ! Función UI
  toggleFigure    --->  TOGGLE FIGURE (activa/desactiva figura geométrica)    ! Función UI
  toggleFrac      --->  TOGGLE FRACtion (alterna modo decimal/fraccionario)   ! Función UI
  togglePanel     --->  TOGGLE PANEL (muestra/oculta panel inferior AL)       ! Función UI
  toggleSection   --->  TOGGLE SECTION (colapsa/expande sección acordeón)    ! Función UI
  triCalc         --->  TRIangle CALCulate (calcula lados/ángulos/área del Δ) ! Función cálculo
  triClear        --->  TRIangle CLEAR (limpia inputs y resultado triángulo)  ! Función UI
  triDrawCanvas   --->  TRIangle DRAW CANVAS (carga P/Q/R al canvas 3D)       ! Función render
  triGet          --->  TRIangle GET (lee coordenadas de input de punto)      ! Función utilitaria
  uN              --->  Update Name (actualiza nombre de vector por ID)       ! Función UI
  uV              --->  Update Vector (actualiza componente + llama rLeg)     ! Función UI
  updUnkName      --->  UPDate UNKnown Name (actualiza nombre de incógnita)   ! Función UI
  updUnkVec       --->  UPDate UNKnown VECtor (actualiza vector incógnita)    ! Función UI
  vc              --->  Vector Color (retorna color de PAL para índice dado)   ! Función utilitaria


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ARCHIVOS DEL PROYECTO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  index.html    —  Estructura HTML: launcher, módulos, formularios, canvas
  style.css     —  Estilos: tokens de diseño, layouts, tarjetas, animaciones
  app.js        —  Lógica: navegación, cálculos, render, PWA, Service Worker
  README.txt    —  Este archivo


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  TOKENS DE DISEÑO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  --al:      #7c6af7   violeta       Álgebra Lineal (principal)
  --al2:     #a594ff   violeta claro Álgebra Lineal (acento)
  --fi:      #22d3ee   cyan          Física
  --fi2:     #67e8f9   cyan claro    Física (acento)
  --ca:      #10b981   esmeralda     Cálculo
  --ca2:     #34d399   esmeralda claro Cálculo (acento)
  --accent:  #f0c040   dorado        Vectores / highlight
  --bg:      #080c14   azul noche    Fondo principal
  --surface: #0d1220   azul oscuro   Superficie de tarjetas
  --surface2:#111827   azul medio    Superficie secundaria
  --border:  #1e2d45   azul borde    Bordes y separadores
  --text1:   #e8f0fc   blanco azulado Texto principal
  --text3:   #3a5a7a   azul grisáceo  Texto terciario / labels


© 2026 xii1rst. Todos los derechos reservados.
Desarrollado con asistencia de Claude (Anthropic).

================================================================================
