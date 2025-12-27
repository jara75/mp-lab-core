🖥️ MP-LAB V1.0 — ESPECIFICACIÓN DE UI/UX Y FLUJO
Concepto: Máquina de Navegación Temporal No es: Un Dashboard de BI Estático

Objetivo: Permitir al consultor visualizar el tiempo como una dimensión navegable y bifurcable.

1. LAYOUT DE PANTALLA PRINCIPAL (CANVAS)

   La pantalla se divide en 4 Zonas Funcionales activas simultáneamente.

   ZONA 1: EL NAVEGADOR TEMPORAL (Top Bar)
   
     ·  Visualización: Timeline horizontal scrollable (Pasado $\leftrightarrow$ Futuro).
   
     ·  Capas de Datos (Curvas Superpuestas):
   
        ·  Lineal: $V(t)$ (Valor Relacional Total).
   
        ·  Lineal: $PRN(t)$ (Patrimonio Relacional Neto).
   
        ·  Eventos: Marcadores verticales para Hitos Reales (Crisis, Lanzamientos, MdV).
   
     ·  Interacción Crítica:
   
        ·  Scroll: Desplazamiento temporal.
   
        ·  Click en fecha $\rightarrow$ FIJAR $t_0$.
   
        ·  Efecto: Esto bloquea la lectura histórica y habilita la simulación futura desde ese punto.

   ZONA 2: SNAPSHOT DE ESTADO (Panel Izquierdo - Read Only)
   
     ·  Comportamiento: Se actualiza instantáneamente al mover el cursor por el timeline. Muestra la "física" del instante seleccionado.
   
     ·  Contenido: Tarjetas de solo lectura con los valores del Vector de Estado en $t_0$.
   
        ·  Identidad: $P$ (Propósito), $A$ (Producto), $S$ (Oferta), $M_{pe}$ (Marca Personizada).
   
        ·  Termodinámica: $U$ (Comunía), $H$ (Habituación), $\Sigma$ (Interferencia).
   
        ·  Dinámica: $V$ (Energía Total), $\Phi$ (Flujo/Velocidad).
   
     ·  UX: Debe transmitir "Datos Congelados". No son celdas editables.

   ZONA 3: CONSOLA DE BIFURCACIÓN (Panel Derecho - Input)

     ·  Contexto: Cambia según el modo seleccionado. Es el único lugar donde el usuario "toca" el sistema.
   
   Modo A: Simulación Estratégica (Predecir)
   
     ·  UI: Panel dividido A/B (Split View) para comparar estrategias.

     ·  Inputs: El usuario inyecta Acciones, no datos numéricos directos.

       ·  Inyectar MdV: (Botón) Simula un evento de alto impacto (resetea $H$).

       ·  Ajustar Tensión: (Slider) Modifica $\Delta R$.

       ·  Campaña de Propósito: (Toggle) Reactiva el vector $P$.Feedback: Al modificar, el gráfico futuro (Zona 4) se actualiza en tiempo real.

     ·  Feedback: Al modificar, el gráfico futuro (Zona 4) se actualiza en tiempo real.

   Modo B: Calibración (Validar)

     ·  Propósito: Ajustar el modelo para que "encaje" con la historia real.

     ·  Inputs: Sliders de ajuste fino de parámetros ($\alpha, \beta, \lambda$).

     ·  Feedback: Indicador de "Error %" (MSE) que cambia de Rojo a Verde a medida que la curva simulada se superpone a la real.

   ZONA 4: VISOR DE PROYECCIÓN (Overlay Central/Inferior)

     ·  Gráfico Principal:Fan Chart (Gráfico de Abanico Probabilístico).

     ·  Semántica Visual:

       ·  Línea Sólida: La Mediana (Trayectoria más probable).

       ·  Sombreado: Intervalos de confianza (Incertidumbre estocástica).

       ·  Colores: Azul (Escenario A - Control) vs. Rojo (Escenario B - Intervención).

    ·  UX: Debe permitir hacer zoom y ver los valores futuros proyectados al pasar el mouse (tooltip con $t+1, t+2...$).

   2. FLUJO DE USUARIO (USER JOURNEY)
      
     Escenario 1: El Diagnóstico (El Médico)

     1.  Usuario entra y ve la historia completa de la marca (Rastro Relacional).
     2.  Hace scroll y detecta una caída en la curva $V(t)$.
     3.  Hace clic en el punto de inflexión.
     4.  El Snapshot (Zona 2) le revela la causa física: "En este punto, la Habituación ($H$) subió drásticamente y el Flujo ($\Phi$) se detuvo".

    Escenario 2: La Estrategia (El Ajedrecista)
    
     1.  Usuario selecciona "HOY" como $t_0$.
     2.  Activa "Modo Simulación".
     3.  En el Escenario B, pulsa "Inyectar MdV Catalizador" para el mes próximo.
     4.  El Visor (Zona 4) muestra cómo la curva roja se dispara hacia arriba, separándose de la azul (inercial).
     5.  Insight: "Si intervenimos, recuperamos el PRN en 3 meses".

    Escenario 3: La Calibración (El Científico)

     1.  Usuario selecciona una fecha de hace 6 meses.
     2.  Activa "Modo Calibración".
     3.  El sistema proyecta una línea punteada (lo que el modelo cree que pasó) sobre la línea sólida (lo que realmente pasó).
     4.  Usuario ajusta la sensibilidad $\alpha$ hasta que las líneas coinciden.
     5.  Resultado: El modelo ha "aprendido" la física específica de esta marca.

  3.  ESTILO VISUAL Y FEELING

    ·  Tema: Dark Mode preferente (Estética de Laboratorio/Ingeniería, no de Marketing).
    
    ·  Tipografía: Monospace para datos (estilo terminal), Sans-serif limpia para etiquetas.
    
    ·  Colores Semánticos:
    
        ·  Energía/Valor ($V, E$) = Dorado/Amarillo.
        
        ·  Comunía ($U$) = Cian/Azul Eléctrico.
        
        ·  Riesgo/Entropía ($H, \Sigma$) = Rojo/Naranja.
    
    ·  Animación: Transiciones suaves al mover el tiempo. Los números no "saltan", fluyen como un contador analógico.
