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

La unidad fundamental de la DB no es el "Usuario" ni la "Venta". Es el Snapshot del Sistema en un instante $t$.

Estructura JSON del Vector de Estado (VER)

```
{
"timestamp": "ISO-8601 (YYYY-MM-DD)",
  "type": "REAL" | "SIMULATION_A" | "SIMULATION_B",
  "state_vector": {
    "identity": {
      "P": float,       // Magnitud Propósito (0-10)
      "A_S": float,     // Oferta Base (0-10)
      "B": float        // Coherencia (0-1)
    },
    "energy": {
      "V": float,       // Valor Relacional Total
      "U": float,       // Nivel de Comunía
      "PRN": float      // Patrimonio Relacional Neto
    },
    "dynamics": {
      "H": float,       // Tasa de Habituación
      "h_last": float,  // Última Huella registrada
      "sigma": float    // Interferencia externa
    }
  },
  "metadata": {
    "source_event_id": "string", // Link al evento crudo que causó este estado
    "calibration_version": "v1.2" // Qué reglas de traducción se usaron
  }
}
```

3. PIPELINE DE PROCESAMIENTO (THE BACKEND FLOW)

El sistema opera en 4 capas secuenciales estrictas.

CAPA 1: INGESTA & NORMALIZACIÓN (The Cleaning)

·  Input: CSVs, APIs externas (Salesforce, Analytics), Logs manuales.

·  Process: Alineación temporal. Todo se normaliza a una frecuencia base (ej: Diaria o Semanal).

·  Output: Raw_Time_Series_Data.

CAPA 2: MOTOR DE TRADUCCIÓN HEURÍSTICA (The IP Core)

·Input: Raw_Data + Translation_Rules (Configuración del Consultor).

·Logic: Mapeo de métricas físicas a variables metafísicas.

  ·  Regla Ej: IF (BounceRate > 60%) THEN (H += 0.05)

  ·  Regla Ej: IF (NPS_Promoter > 70) THEN (U += 0.1)

·  Output: Historical_State_Vectors (La "Verdad" del sistema).

CAPA 3: MOTOR DE SIMULACIÓN (The Oracle)

·  Input: State_Vector(t0) + Intervention_Vector (Acciones del usuario).

·  Logic: Monte Carlo + Cadenas de Markov.

  1.  Clonar estado $t_0$.

  2.  Aplicar Intervention (ej: inyectar MdV).

  3.  Iterar $N$ pasos de tiempo usando Matriz de Transición $M(E)$.

  4.  Repetir 1,000 veces para generar varianza.

Output: Probabilistic_Fan_Chart (Percentiles 5, 50, 95).

CAPA 4: MÓDULO DE CALIBRACIÓN (The Scientist)

·  Logic: Comparación de curvas ($Curve_{Sim}$ vs $Curve_{Real}$).

·  Loop: Ajuste de coeficientes ($\alpha, \beta, \gamma$) mediante descenso de gradiente o ajuste manual hasta minimizar el error cuadrático medio (MSE).

4. ARQUITECTURA TÉCNICA SUGERIDA (STACK)

| Componente              | Tecnología Recomendada              | Justificación                                                                  |
| :---                    | :---                                | :---                                                                           |
| Backend Calculation     | Python (FastAPI + NumPy/Pandas)     | Necesario para cálculo matricial pesado y Monte Carlo.                         |
| API Layer               | GraphQL                             | Permite pedir solo los campos necesarios del Vector de Estado complejo.        |
| Database                | PostgreSQL (JSONB) o TimeScaleDB    | Manejo eficiente de series temporales y estructuras JSON complejas.            |
| Frontend State          | Redux / Pinia (Store)               | El "Snapshot" debe vivir en el store global del cliente para navegación rápida.|
| Versioning              | Git-like Logic (Custom)             | Implementar lógica de ramas (Master/Branch) para los escenarios.               |


5. DEFINICIÓN DE "DONE" (CRITERIOS DE ACEPTACIÓN)

El sistema se considera funcionalmente correcto solo si:

1.  Reversibilidad: Puedo ir a cualquier fecha $t$ del pasado y ver el estado exacto de ese día.

2.  Causalidad: Una simulación futura NUNCA altera un registro histórico.

3.  Falsabilidad: El sistema permite superponer una simulación sobre el pasado para ver el error (Backtesting).

4.  Consistencia: La suma de probabilidades de Markov siempre da 100%.

____________________


