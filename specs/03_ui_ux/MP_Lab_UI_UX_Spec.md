🖥️ MP-LAB V1.0 — ESPECIFICACIÓN DE UI/UX Y FLUJO

Concepto: Máquina de Navegación Temporal
No es: Un Dashboard de BI Estático

1. LAYOUT DE PANTALLA PRINCIPAL (CANVAS)

La pantalla se divide en 4 Zonas Funcionales activas simultáneamente.

ZONA 1: EL NAVEGADOR TEMPORAL (Top Bar)

Visualización: Timeline horizontal scrollable (Pasado $\leftrightarrow$ Futuro).

Capas de Datos: Curvas $V(t)$, $PRN(t)$ y Marcadores de Eventos.

Interacción Crítica:

Click en fecha $\rightarrow$ FIJAR $t_0$.

Esto bloquea la lectura histórica y habilita la simulación futura.

ZONA 2: SNAPSHOT DE ESTADO (Panel Izquierdo - Read Only)

Comportamiento: Se actualiza instantáneamente al mover el timeline.

Contenido: Tarjetas de solo lectura con los valores del Vector de Estado en $t_0$.

Identidad ($P, A, B$).

Energía ($V, U, PRN$).

Dinámica ($H, h$).

UX: Debe transmitir "Datos Congelados". No editables.

ZONA 3: CONSOLA DE BIFURCACIÓN (Panel Derecho - Input)

Contexto: Cambia según el modo seleccionado.

Modo A: Simulación Estratégica (Predecir)

UI: Panel dividido A/B (Split View).

Inputs: Acciones (Botones/Sliders), NO datos.

Inyectar MdV (Botón).

Ajustar Tensión (Slider).

Feedback: Al modificar, el gráfico futuro se actualiza en tiempo real (o on-release).

Modo B: Calibración (Validar)

Inputs: Sliders de ajuste fino ($\alpha, \beta, \lambda$).

Feedback: Indicador de "Error %" que cambia de Rojo a Verde a medida que las curvas se alinean.

ZONA 4: VISOR DE PROYECCIÓN (Overlay Central/Inferior)

Gráfico Principal: Fan Chart (Abanico).

Semántica:

Línea Sólida = Mediana.

Sombra = Incertidumbre.

Azul = Escenario A / Rojo = Escenario B.

UX: Debe permitir hacer zoom y ver los valores futuros proyectados al pasar el mouse (tooltip).

2. FLUJO DE USUARIO (USER JOURNEY)

Escenario 1: El Diagnóstico

Usuario entra y ve la historia completa de la marca.

Hace scroll y detecta una caída en la curva $V(t)$.

Hace clic en el punto de inflexión.

El Snapshot (Zona 2) le muestra: "Ah, claro, aquí subió la Habituación ($H$) y bajó la Comunía ($U$)".

Escenario 2: La Estrategia (What-If)

Usuario selecciona "HOY" ($t_0$).

Activa "Modo Simulación".

En el Escenario B, pulsa "Inyectar MdV Catalizador" en el mes próximo.

El Visor (Zona 4) muestra cómo la curva roja se dispara hacia arriba, separándose de la azul (inercial).

Usuario exporta el gráfico para el cliente: "Esto es lo que pasa si intervenimos".

Escenario 3: La Calibración (Ciencia)

Usuario selecciona una fecha de hace 6 meses.

Activa "Modo Calibración".

El sistema proyecta una línea punteada (simulación vieja) que no calza con la línea sólida (realidad).

Usuario ajusta $\alpha$ (sensibilidad) hasta que las líneas se superponen perfectamente.

Guarda la configuración: "Ahora el modelo entiende a esta marca".

3. ESTILO VISUAL Y FEELING

Tema: Dark Mode preferente (Laboratorio/Ingeniería).

Colores: Semánticos.

Energía/Valor = Dorado/Amarillo.

Comunía = Cian/Azul.

Riesgo/Entropía = Rojo/Naranja.

Animación: Transiciones suaves al mover el tiempo. Los números no "saltan", fluyen.
