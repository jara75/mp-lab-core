🧬 MP-LAB V1.0 — BLUEPRINT DE ARQUITECTURA DE SOFTWARE

Paradigma: State-Centric Simulation Engine
Core Logic: Marcaje Personizante (MP) V10.1
Target: Google Antigravity Dev Team

1. PRINCIPIOS DE INGENIERÍA (THE MANIFESTO)

  1.  State over Metrics: No guardamos métricas sueltas. Guardamos Vectores de Estado Relacional (VER) completos asociados a un timestamp $t$.

  2.  Immutable History: El pasado (Rastro Relacional) es Read-Only. La base de datos histórica es un append-only log de estados confirmados.

  3.  Multiverse Branching: La simulación no sobreescribe datos. Crea "ramas" temporales (Branch A, Branch B) divergentes desde un $t_0$, estilo Git.

  4.  Stochastic Output: El backend nunca devuelve un escalar único para el futuro. Devuelve tensores de probabilidad (arrays de distribución).

2. MODELO DE DATOS (THE ATOMIC UNIT)

La unidad fundamental de la DB no es el "Usuario" ni la "Venta". La unidad fundamental de la DB es el Snapshot del Sistema en un instante $t$. Este objeto contiene dos estructuras separadas: el Vector de Estado Relacional (Resultado de Navegación) y las Variables del Sistema (Motores de Cálculo).

```
  {
  "timestamp": "ISO-8601 (YYYY-MM-DD)",
  "type": "REAL" | "SIMULATION_A" | "SIMULATION_B",

  // 1. EL VECTOR DE ESTADO RELACIONAL (Vs) - El Output Físico (Apendice V10.1 Sec 6.2)
  // Representa la ubicación y cinética de la marca en el espacio relacional.
  "relational_state_vector_Vs": {
    "x_position": "string",   // Posición: Estado en la taxonomía (ej: 'Retractor', 'Indiferente', 'Prospecto')
    "E_energy": "float",      // Energía: Nivel de PRN (Patrimonio Relacional Neto acumulado)
    "p_momentum": "float"     // Momento: Velocidad de cambio o Inercia del sistema
  },

  // 2. VARIABLES DEL SISTEMA - Los Inputs del Motor Físico
  // Son los parámetros termodinámicos que generan el vector anterior.
  "system_physics_variables": {
    "identity_mechanics": {
      "P_purpose": "float",       // Magnitud Propósito (Fuerza Negentrópica)
      "A_producto": "float",    // Valor de Atributos
      "S_": "float",       // Valor de Oferta (Amor, Respeto, Transparencia)
      "Mpe_coherence": "float"    // Coherencia (Coseno de Theta Índice de Integridad, 0-1)
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

```

3. PIPELINE DE PROCESAMIENTO (THE BACKEND FLOW)

El sistema opera en 4 capas secuenciales estrictas.

CAPA 1: INGESTA & NORMALIZACIÓN (The Cleaning)

  ·  Input: CSVs, APIs externas (Salesforce, Analytics), Logs manuales.

  ·  Process: Alineación temporal. Todo se normaliza a una frecuencia base (ej: Diaria, Semanal o mensual).

  ·  Output: Raw_Time_Series_Data.

CAPA 2: MOTOR DE TRADUCCIÓN HEURÍSTICA (The IP Core)

  ·  Input: Raw_Data + Translation_Rules (Configuración del Consultor).

  ·  Logic: Mapeo de métricas físicas a variables metafísicas del bloque system_physics_variables..

  ·  Output: Historical_State_Vectors (La "Verdad" del sistema).
_____

| Métrica de Origen (Input)       | Variable MP Afectada (Output)       | Lógica de Traducción (Ejemplo)                                 |
| :---                            | :---                                | :---                                                           |
| NPS (Promotores)                | U (Comunía)                         | Si NPS > 50, U += 0.2 (Inyección de temperatura).              |
| Churn Rate (Tasa de Abandono)   | H (Habituación)                     | Si Churn sube, H tiende a 1 (Enfriamiento acelerado).          |
| Share of Voice (Competencia)    | Σ (Interferencia)                   | Si SoV Competencia sube, Sigma aumenta (Mayor resistencia).    |
| Campaña de Manifiesto           | P (Propósito)                       | Evento binario: Reactiva el vector P (Fuerza Negentrópica).    |
| Quejas / Tickets de Soporte     | Mpe (Coherencia)                    | Si Quejas suben > 10%, Mpe baja (Incoherencia percibida).      |
| Tiempo sin Interacción          | H (Habituación)                     | Función de decaimiento: H = 1 - e^(-lambda * tiempo).          |

·  Output: System_Variables_History.

_____

CAPA 3: MOTOR DE SIMULACIÓN Y CÁLCULO (The Oracle)

·  Input: System_Variables(t) + Intervention.

·  Logic: Algoritmo Híbrido (Monte Carlo + Física V10.1).

    1.  Clonación ($t_0$): Se toma el estado inicial validado.
    
    2.  Bucle Monte Carlo (x1000 iteraciones):
    
      ·  Para cada iteración $i$, se simula una trayectoria temporal $t \rightarrow t_{end}$.
      ·  Paso de Tiempo (Kernel V10.1): En cada mes $t$, se resuelve:
      
          ·  $V(t)$ (Ecuación Maestra con ruido estocástico en $\Sigma$).
          ·  Integración de $\Phi$ para obtener Energía $E$ (PRN).
          
          ·  Derivación de Momento $p$.
          
          ·  Transición de Estado $x$ (Matriz Markoviana dependiente de $V$).
          
    3.  Agregación: Se consolidan las 1000 trayectorias para calcular percentiles (5%, 50%, 95%).
    
·  Output: Probabilistic_Fan_Chart (Abanico de Futuros Probables).

CAPA 4: MÓDULO DE CALIBRACIÓN (The Scientist)

·  Logic: Comparación de curvas ($Curve_{Sim}$ vs $Curve_{Real}$).

·  Loop: Ajuste de coeficientes ($\alpha, \beta, \gamma$) mediante descenso de gradiente o ajuste manual hasta minimizar el error cuadrático medio (MSE).

4. ARQUITECTURA TÉCNICA SUGERIDA (STACK)

| Componente              | Tecnología Recomendada              | Justificación                                                                  |
| :---                    | :---                                | :---                                                                           |
| Backend Calculation     | Python (FastAPI + NumPy/Pandas)     | Necesario para cálculo matricial pesado y Monte Carlo.                         |
| API Layer               | GraphQL                             | Permite pedir solo los campos necesarios del Vector de Estado complejo.        |
| Database                | PostgreSQL (JSONB) o TimeScaleDB    | Manejo eficiente de series temporales y estructuras JSON complejas.            |
| Frontend State          | React / Redux / Pinia (Store)       | El "Snapshot" debe vivir en el store global del cliente para navegación rápida.|
| Versioning              | Git-like Logic (Custom)             | Implementar lógica de ramas (Master/Branch) para los escenarios.               |


5. DEFINICIÓN DE "DONE" (CRITERIOS DE ACEPTACIÓN)

El sistema se considera funcionalmente correcto solo si:

1.  Reversibilidad: Puedo ir a cualquier fecha $t$ del pasado y ver el estado exacto de ese día.

2.  Causalidad: Una simulación futura NUNCA altera un registro histórico.

3.  Falsabilidad: El sistema permite superponer una simulación sobre el pasado para ver el error (Backtesting).

4.  Consistencia: La suma de probabilidades de Markov siempre da 100%.

____________________

Especificación generada por El Marcante V2 -
