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

______

🧬 MP-LAB V1.0 — BLUEPRINT DE ARQUITECTURA DE SOFTWAREParadigma: State-Centric Simulation EngineCore Logic: Marcaje Personizante (MP) V10.1Target: Google Antigravity Dev Team1. PRINCIPIOS DE INGENIERÍA (THE MANIFESTO)State over Metrics: No guardamos métricas sueltas. Guardamos Vectores de Estado Relacional (VER) completos asociados a un timestamp t.Immutable History: El pasado (Rastro Relacional) es Read-Only. La base de datos histórica es un append-only log de estados confirmados.Multiverse Branching: La simulación no sobreescribe datos. Crea "ramas" temporales (Branch A, Branch B) divergentes desde un t0, estilo Git.Stochastic Output: El backend nunca devuelve un escalar único para el futuro. Devuelve tensores de probabilidad (arrays de distribución).2. MODELO DE DATOS (THE ATOMIC UNIT)La unidad fundamental de la DB es el Snapshot del Sistema en un instante t. Este objeto contiene dos estructuras separadas: el Vector de Estado Físico (Resultado de Navegación) y las Variables del Sistema (Motores de Cálculo).Estructura JSON del Snapshot (Snapshot_t){
  "timestamp": "ISO-8601 (YYYY-MM-DD)",
  "type": "REAL" | "SIMULATION_A" | "SIMULATION_B",

  // 1. EL VECTOR DE ESTADO RELACIONAL (Vs) - El Output Físico (Apendice V10.1 Sec 6.2)
  // Representa la ubicación y cinética de la marca en el espacio relacional.
  "relational_state_vector_Vs": {
    "x_position": "string",   // Posición: Estado en la taxonomía (ej: 'Cliente Fiel', 'Indiferente')
    "E_energy": "float",      // Energía: Nivel de PRN (Patrimonio Relacional Neto acumulado)
    "p_momentum": "float"     // Momento: Velocidad de cambio o Inercia del sistema
  },

  // 2. VARIABLES DEL SISTEMA - Los Inputs del Motor Físico
  // Son los parámetros termodinámicos que generan el vector anterior.
  "system_physics_variables": {
    "identity_mechanics": {
      "P_purpose": "float",       // Magnitud Propósito (Fuerza Negentrópica)
      "A_product": "float",       // Valor de Producto (Intrínseco + Consustancial)
      "S_offer": "float",         // Valor de Oferta (Acceso + Dignidad)
      "Mpe_coherence": "float"    // Coherencia (Índice de Integridad, 0-1)
    },
    "thermodynamics": {
      "U_comunia": "float",       // Temperatura del vínculo
      "H_habituation": "float",   // Tasa de entropía interna
      "Sigma_interference": "float" // Tasa de entropía externa (Ruido)
    },
    "calculated_flow": {
      "V_total_value": "float",   // Valor Relacional Total (V3)
      "Phi_flow": "float",        // Flujo instantáneo (Derivada)
      "Delta_R_tension": "float"  // Tensión Nodal
    }
  },

  "metadata": {
    "source_event_id": "string",
    "calibration_profile_id": "v1.2"
  }
}
3. PIPELINE DE PROCESAMIENTO (THE BACKEND FLOW)El sistema opera en 4 capas secuenciales estrictas.CAPA 1: INGESTA & NORMALIZACIÓN (The Cleaning)Input: CSVs, APIs externas (Salesforce, Analytics), Logs manuales.Process: Alineación temporal. Todo se normaliza a una frecuencia base (ej: Diaria o Semanal).Output: Raw_Time_Series_Data.CAPA 2: MOTOR DE TRADUCCIÓN HEURÍSTICA (The IP Core)Input: Raw_Data + Translation_Rules (Configuración del Consultor).Logic: Mapeo de métricas físicas a variables metafísicas del bloque system_physics_variables.Tabla de Traducción Estándar (Default Mapping):| Métrica de Origen (Input)       | Variable MP Afectada (Output)       | Lógica de Traducción (Ejemplo)                                 |
| :---                            | :---                                | :---                                                           |
| NPS (Promotores)                | U (Comunía)                         | Si NPS > 50, U += 0.2 (Inyección de temperatura).              |
| Churn Rate (Tasa de Abandono)   | H (Habituación)                     | Si Churn sube, H tiende a 1 (Enfriamiento acelerado).          |
| Share of Voice (Competencia)    | Σ (Interferencia)                   | Si SoV Competencia sube, Sigma aumenta (Mayor resistencia).    |
| Campaña de Manifiesto           | P (Propósito)                       | Evento binario: Reactiva el vector P (Fuerza Negentrópica).    |
| Quejas / Tickets de Soporte     | Mpe (Coherencia)                    | Si Quejas suben > 10%, Mpe baja (Incoherencia percibida).      |
| Tiempo sin Interacción          | H (Habituación)                     | Función de decaimiento: H = 1 - e^(-lambda * tiempo).          |
Output: System_Variables_History.CAPA 3: MOTOR DE SIMULACIÓN Y CÁLCULO (The Oracle)Input: System_Variables(t) + Intervention.Logic: Algoritmo Híbrido (Monte Carlo + Física V10.1).Clonación (t0): Se toma el estado inicial validado.Bucle Monte Carlo (x1000 iteraciones):Para cada iteración i, se simula una trayectoria temporal t -> tend.Paso de Tiempo (Kernel V10.1): En cada mes t, se resuelve:V(t) (Ecuación Maestra con ruido estocástico en Sigma).Integración de Phi para obtener Energía E (PRN).Derivación de Momento p.Transición de Estado x (Matriz Markoviana dependiente de V).Agregación: Se consolidan las 1000 trayectorias para calcular percentiles (5%, 50%, 95%).Output: Probabilistic_Fan_Chart (Abanico de Futuros Probables).CAPA 4: MÓDULO DE CALIBRACIÓN (The Scientist)Logic: Comparación de curvas (Curve_Sim vs Curve_Real).Loop: Ajuste de coeficientes (alpha, beta, gamma) mediante descenso de gradiente o ajuste manual hasta minimizar el error cuadrático medio (MSE).4. ARQUITECTURA TÉCNICA SUGERIDA (STACK)| Componente              | Tecnología Recomendada              | Justificación                                                                  |
| :---                    | :---                                | :---                                                                           |
| Backend Calculation     | Python (FastAPI + NumPy/Pandas)     | Necesario para cálculo matricial pesado y Monte Carlo.                         |
| API Layer               | GraphQL                             | Permite pedir solo los campos necesarios del Vector de Estado complejo.        |
| Database                | PostgreSQL (JSONB) o TimeScaleDB    | Manejo eficiente de series temporales y estructuras JSON complejas.            |
| Frontend Framework      | React.js / Vue.js                   | Estándar de industria para SPAs complejas y reactivas.                         |
| Frontend State          | Redux / Pinia (Store)               | El "Snapshot" debe vivir en el store global del cliente para navegación rápida.|
| Versioning              | Git-like Logic (Custom)             | Implementar lógica de ramas (Master/Branch) para los escenarios.               |
5. DEFINICIÓN DE "DONE" (CRITERIOS DE ACEPTACIÓN)El sistema se considera funcionalmente correcto solo si:Reversibilidad: Puedo ir a cualquier fecha t del pasado y ver el estado exacto de ese día.Causalidad: Una simulación futura NUNCA altera un registro histórico.Falsabilidad: El sistema permite superponer una simulación sobre el pasado para ver el error (Backtesting).Consistencia: La suma de probabilidades de Markov siempre da 100%.
