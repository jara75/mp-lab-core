🖥️ MP-LAB V1.0 — ESPECIFICACIÓN DE UI/UX Y FLUJO

Concepto: Máquina de Navegación Temporal
No es: Un Dashboard de BI Estático

1. LAYOUT DE PANTALLA PRINCIPAL (CANVAS)

La pantalla se divide en 4 Zonas Funcionales activas simultáneamente.

ZONA 1: EL NAVEGADOR TEMPORAL (Top Bar)

Visualización: Timeline horizontal scrollable (Pasado $\leftrightarrow$ Futuro).

Capas de Datos (Curvas Superpuestas):

Lineal: $V(t)$ (Valor Relacional Total).

Lineal: $PRN(t)$ (Patrimonio Relacional Neto).

Eventos: Marcadores verticales para Hitos Reales (Crisis, Lanzamientos, MdV).

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

______

🖥️ MP-LAB V1.0 — ESPECIFICACIÓN DE UI/UX Y FLUJOConcepto: Máquina de Navegación TemporalNo es: Un Dashboard de BI EstáticoObjetivo: Permitir al consultor visualizar el tiempo como una dimensión navegable y bifurcable.1. LAYOUT DE PANTALLA PRINCIPAL (CANVAS)La pantalla se divide en 4 Zonas Funcionales activas simultáneamente.ZONA 1: EL NAVEGADOR TEMPORAL (Top Bar)Visualización: Timeline horizontal scrollable (Pasado $\leftrightarrow$ Futuro).Capas de Datos (Curvas Superpuestas):Lineal: $V(t)$ (Valor Relacional Total).Lineal: $PRN(t)$ (Patrimonio Relacional Neto).Eventos: Marcadores verticales para Hitos Reales (Crisis, Lanzamientos, MdV).Interacción Crítica:Scroll: Desplazamiento temporal.Click en fecha $\rightarrow$ FIJAR $t_0$.Efecto: Esto bloquea la lectura histórica y habilita la simulación futura desde ese punto.ZONA 2: SNAPSHOT DE ESTADO (Panel Izquierdo - Read Only)Comportamiento: Se actualiza instantáneamente al mover el cursor por el timeline. Muestra la "física" del instante seleccionado.Contenido: Tarjetas de solo lectura con los valores del Vector de Estado en $t_0$.Identidad: $P$ (Propósito), $A$ (Producto), $S$ (Oferta), $M_{pe}$ (Marca Personizada).Termodinámica: $U$ (Comunía), $H$ (Habituación), $\Sigma$ (Interferencia).Dinámica: $V$ (Energía Total), $\Phi$ (Flujo/Velocidad).UX: Debe transmitir "Datos Congelados". No son celdas editables.ZONA 3: CONSOLA DE BIFURCACIÓN (Panel Derecho - Input)Contexto: Cambia según el modo seleccionado. Es el único lugar donde el usuario "toca" el sistema.Modo A: Simulación Estratégica (Predecir)UI: Panel dividido A/B (Split View) para comparar estrategias.Inputs: El usuario inyecta Acciones, no datos numéricos directos.Inyectar MdV: (Botón) Simula un evento de alto impacto (resetea $H$).Ajustar Tensión: (Slider) Modifica $\Delta R$.Campaña de Propósito: (Toggle) Reactiva el vector $P$.Feedback: Al modificar, el gráfico futuro (Zona 4) se actualiza en tiempo real.Modo B: Calibración (Validar)Propósito: Ajustar el modelo para que "encaje" con la historia real.Inputs: Sliders de ajuste fino de parámetros ($\alpha, \beta, \lambda$).Feedback: Indicador de "Error %" (MSE) que cambia de Rojo a Verde a medida que la curva simulada se superpone a la real.ZONA 4: VISOR DE PROYECCIÓN (Overlay Central/Inferior)Gráfico Principal: Fan Chart (Gráfico de Abanico Probabilístico).Semántica Visual:Línea Sólida: La Mediana (Trayectoria más probable).Sombreado: Intervalos de confianza (Incertidumbre estocástica).Colores: Azul (Escenario A - Control) vs. Rojo (Escenario B - Intervención).UX: Debe permitir hacer zoom y ver los valores futuros proyectados al pasar el mouse (tooltip con $t+1, t+2...$).2. FLUJO DE USUARIO (USER JOURNEY)Escenario 1: El Diagnóstico (El Médico)Usuario entra y ve la historia completa de la marca (Rastro Relacional).Hace scroll y detecta una caída en la curva $V(t)$.Hace clic en el punto de inflexión.El Snapshot (Zona 2) le revela la causa física: "En este punto, la Habituación ($H$) subió drásticamente y el Flujo ($\Phi$) se detuvo".Escenario 2: La Estrategia (El Ajedrecista)Usuario selecciona "HOY" como $t_0$.Activa "Modo Simulación".En el Escenario B, pulsa "Inyectar MdV Catalizador" para el mes próximo.El Visor (Zona 4) muestra cómo la curva roja se dispara hacia arriba, separándose de la azul (inercial).Insight: "Si intervenimos, recuperamos el PRN en 3 meses".Escenario 3: La Calibración (El Científico)Usuario selecciona una fecha de hace 6 meses.Activa "Modo Calibración".El sistema proyecta una línea punteada (lo que el modelo cree que pasó) sobre la línea sólida (lo que realmente pasó).Usuario ajusta la sensibilidad $\alpha$ hasta que las líneas coinciden.Resultado: El modelo ha "aprendido" la física específica de esta marca.3. ESTILO VISUAL Y FEELINGTema: Dark Mode preferente (Estética de Laboratorio/Ingeniería, no de Marketing).Tipografía: Monospace para datos (estilo terminal), Sans-serif limpia para etiquetas.Colores Semánticos:Energía/Valor ($V, E$) = Dorado/Amarillo.Comunía ($U$) = Cian/Azul Eléctrico.Riesgo/Entropía ($H, \Sigma$) = Rojo/Naranja.Animación: Transiciones suaves al mover el tiempo. Los números no "saltan", fluyen como un contador analógico.
