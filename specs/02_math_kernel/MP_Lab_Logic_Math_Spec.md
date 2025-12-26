🧮 MP-LAB V1.0 — ESPECIFICACIÓN DE LÓGICA Y MATEMÁTICA

Propósito: Definir las reglas de negocio y ecuaciones que gobiernan la simulación.
Base Oficial: Apéndice Académico V10.1 (Corregido) - Dinámica de Vorticidad Relacional.

1. DICCIONARIO DE VARIABLES (EL LENGUAJE DEL SISTEMA)

Símbolo

Variable / Descripción

Naturaleza

Definición Operativa / Psicológica

$A$

Atributos del producto

Material

Valor intrínseco tangible y funcional.

$S$

Oferta de servicio

Material

Condiciones de acceso y desempeño.

$M_{pe}$

Coherencia

Relacional

Alineación identitaria (Cálculo trigonométrico).

$U(t)$

Comunía

Clima

Habitabilidad y escudo contra la interferencia.

$P$

Propósito

Vectorial

Fuerza negentrópica activa (Sentido).

$\Sigma$

Interferencia Externa

Entrópica

Ruido, competencia y saturación ambiental.

$V(t)$

Valor Personizante

Sistémica

Nivel energético global del sistema.

$\Phi(t)$

Flujo Relacional

Dinámica

Intercambio instantáneo de valor.

$PRN(t)$

Patrimonio Relacional

Acumulativa

Capital histórico (Brand Equity).

$H(t)$

Habituación

Entrópica

Memoria entrópica por monotonía (Aburrimiento).

$R_{MP}$

Resistencia Activa

Identidad

Fuerza de coherencia interna y voluntad de ser.

$R_{P}$

Resistencia Pasiva

Entropía

Inercia del mercado, cinismo, escepticismo.

$\Delta R$

Diferencial de Resistencia

Motor

Generador de Tensión Nodal ($R_{MP} - R_{P}$).

$\eta$

Conversión Patrimonial

Empírico

Coeficiente de acoplamiento financiero.

2. ECUACIONES MAESTRAS (EL KERNEL FÍSICO)

El backend debe implementar estas ecuaciones exactas para calcular el estado en cada paso de tiempo $t$.

A. Ecuación General del Valor ($V_{10.1}$)

La fórmula integra Potencial, Propósito, Protección Ambiental y Memoria Histórica.

$$V(t) = \left[ (A+S) \cdot M_{pe} \cdot e^{\alpha U(t)} \right] \cdot \underbrace{\frac{e^{\beta P}}{1 + \Sigma e^{-\gamma U(t)}}}_{\text{Factor Elevador & Escudo}} + \underbrace{\eta \int_{t_0}^{t} \Phi(\tau) d\tau}_{\text{Patrimonio (Memoria)}}$$

Nota Dev: El término integral se computa iterativamente como PRN_new = PRN_old + (Phi_t * delta_t * eta).

B. Dinámica de Flujo Instantáneo ($\Phi$)

El flujo de valor no es constante; depende de la Tensión Nodal y la Energía Relacional disponible.

$$\Phi(t) = \frac{\text{sgn}(\Delta R(t)) \cdot ER(t)}{T_{nodal}(t) + \epsilon}$$

Donde la Energía Relacional Activa ($ER$) está condicionada por la Habituación:

$$ER(t) = k \cdot T_{nodal}(t) \cdot [1 - H(t)] \cdot e^{-\Delta t / \tau}$$

Interpretación: Si la Habituación $H(t)$ llega a 1 (aburrimiento total), la Energía $ER$ cae a 0, y el Flujo $\Phi$ se detiene.

C. Función de Coherencia ($M_{pe}$)

Calculada trigonométricamente mediante producto punto de vectores normalizados.

$$M_{pe} = \cos(\theta) = \frac{\vec{v}_{d} \cdot \vec{v}_{p}}{|\vec{v}_{d}| \cdot |\vec{v}_{p}|}$$

Rango:

$1.0$: Coherencia Total ($0^\circ$).

$0.0$: Irrelevancia ($90^\circ$).

$-1.0$: Incoherencia/Traición ($180^\circ$).

D. Ley de Habituación ($H$)

Modelado del decaimiento del interés en ausencia de novedades (Momentos de la Verdad).

$$H(t) = 1 - e^{-\lambda_h (t - t_{last\_MdV})}$$

Trigger: Un nuevo MdV resetea $t_{last\_MdV}$ al tiempo actual, haciendo que $H(t)$ caiga a 0 instantáneamente (reactivación).

3. LÓGICA DE SIMULACIÓN Y TRANSICIÓN

Motor Markoviano (Dependiente de Energía)

Las probabilidades de transición en la matriz $M$ no son estáticas. Dependen de si la energía supera un umbral de activación (Efecto Túnel).

$$P_{i \to j} \propto \exp\left( \frac{\Delta R(t) \cdot \kappa_{ij}}{\text{dist}(i,j)^\gamma} \right)$$

Regla de Negocio: Si $ER(t) > E_{critico}$, se habilitan transiciones no-lineales (saltos directos de "Indiferente" a "Fiel").

Condiciones de Estabilidad (Watchdog)

El sistema debe alertar si la simulación entra en zonas inestables:

Muerte Térmica: Si $T_{nodal} \approx 0$. (Sistema estático).

Ruptura: Si $T_{nodal} > T_{critico}$. (Conflicto abierto).

4. VALIDACIÓN DE CALIBRACIÓN (BACKTESTING)

Para el módulo de calibración (Capa 9), el error se minimiza comparando la curva simulada con la real, ajustando los coeficientes libres:

$\alpha$ (Sensibilidad a Comunía)

$\beta$ (Sensibilidad a Propósito)

$\gamma$ (Eficacia del Escudo)

$\lambda_h$ (Velocidad de olvido)

$$MSE = \frac{1}{n} \sum (V_{sim} - V_{real})^2$$

Especificación generada por El Marcante V2 - Basada estrictamente en Apéndice V10.1.

🧮 MP-LAB V1.0 — ESPECIFICACIÓN DE LÓGICA Y MATEMÁTICAPropósito: Definir las reglas de negocio y ecuaciones que gobiernan la simulación.Base Oficial: Apéndice Académico V10.1 (Corregido) - Dinámica de Vorticidad Relacional.1. DICCIONARIO DE VARIABLES (EL LENGUAJE DEL SISTEMA)SímboloVariable / DescripciónNaturalezaDefinición Operativa / Psicológica$A$Atributos del productoMaterialValor intrínseco tangible y funcional.$S$Oferta de servicioMaterialCondiciones de acceso y desempeño.$M_{pe}$CoherenciaRelacionalAlineación identitaria (Cálculo trigonométrico).$U(t)$ComuníaClimaHabitabilidad y escudo contra la interferencia.$P$PropósitoVectorialFuerza negentrópica activa (Sentido).$\Sigma$Interferencia ExternaEntrópicaRuido, competencia y saturación ambiental.$V(t)$Valor PersonizanteSistémicaNivel energético global del sistema.$\Phi(t)$Flujo RelacionalDinámicaIntercambio instantáneo de valor.$PRN(t)$Patrimonio RelacionalAcumulativaCapital histórico (Brand Equity).$H(t)$HabituaciónEntrópicaMemoria entrópica por monotonía (Aburrimiento).$R_{MP}$Resistencia ActivaIdentidadFuerza de coherencia interna y voluntad de ser.$R_{P}$Resistencia PasivaEntropíaInercia del mercado, cinismo, escepticismo.$\Delta R$Diferencial de ResistenciaMotorGenerador de Tensión Nodal ($R_{MP} - R_{P}$).$\eta$Conversión PatrimonialEmpíricoCoeficiente de acoplamiento financiero.2. ECUACIONES MAESTRAS (EL KERNEL FÍSICO)El backend debe implementar estas ecuaciones exactas para calcular el estado en cada paso de tiempo $t$.A. Ecuación General del Valor ($V_{10.1}$)La fórmula integra Potencial, Propósito, Protección Ambiental y Memoria Histórica.$$V(t) = \left[ (A+S) \cdot M_{pe} \cdot e^{\alpha U(t)} \right] \cdot \underbrace{\frac{e^{\beta P}}{1 + \Sigma e^{-\gamma U(t)}}}_{\te$$V(t) = \left[ (A+S) \cdot M_{pe} \cdot e^{\alpha U(t)} \right] \cdot \underbrace{\frac{e^{\beta P}}{1 + \Sigma e^{-\gamma U(t)}}}_{\text{Factor Elevador & Escudo}} + \underbrace{\eta \int_{t_0}^{t} \Phi(\tau) d\tau}_{\text{Patrimonio (Memoria)}}$$xt{Factor Elevador & Escudo}} + \underbrace{\eta \int_{t_0}^{t} \Phi(\tau) d\tau}_{\text{Patrimonio (Memoria)}}$$Nota Dev: El término integral se computa iterativamente como PRN_new = PRN_old + (Phi_t * delta_t * eta).B. Dinámica de Flujo Instantáneo ($\Phi$)El flujo de valor no es constante; depende de la Tensión Nodal y la Energía Relacional disponible.$$\Phi(t) = \frac{\text{sgn}(\Delta R(t)) \cdot ER(t)}{T_{nodal}(t) + \epsilon}$$Donde la Energía Relacional Activa ($ER$) está condicionada por la Habituación:$$ER(t) = k \cdot T_{nodal}(t) \cdot [1 - H(t)] \cdot e^{-\Delta t / \tau}$$Interpretación: Si la Habituación $H(t)$ llega a 1 (aburrimiento total), la Energía $ER$ cae a 0, y el Flujo $\Phi$ se detiene.C. Función de Coherencia ($M_{pe}$)Calculada trigonométricamente mediante producto punto de vectores normalizados.$$M_{pe} = \cos(\theta) = \frac{\vec{v}_{d} \cdot \vec{v}_{p}}{|\vec{v}_{d}| \cdot |\vec{v}_{p}|}$$Rango:$1.0$: Coherencia Total ($0^\circ$).$0.0$: Irrelevancia ($90^\circ$).$-1.0$: Incoherencia/Traición ($180^\circ$).D. Ley de Habituación ($H$)Modelado del decaimiento del interés en ausencia de novedades (Momentos de la Verdad).$$H(t) = 1 - e^{-\lambda_h (t - t_{last\_MdV})}$$Trigger: Un nuevo MdV resetea $t_{last\_MdV}$ al tiempo actual, haciendo que $H(t)$ caiga a 0 instantáneamente (reactivación).3. LÓGICA DE SIMULACIÓN Y TRANSICIÓNMotor Markoviano (Dependiente de Energía)Las probabilidades de transición en la matriz $M$ no son estáticas. Dependen de si la energía supera un umbral de activación (Efecto Túnel).$$P_{i \to j} \propto \exp\left( \frac{\Delta R(t) \cdot \kappa_{ij}}{\text{dist}(i,j)^\gamma} \right)$$Regla de Negocio: Si $ER(t) > E_{critico}$, se habilitan transiciones no-lineales (saltos directos de "Indiferente" a "Fiel").Condiciones de Estabilidad (Watchdog)El sistema debe alertar si la simulación entra en zonas inestables:Muerte Térmica: Si $T_{nodal} \approx 0$. (Sistema estático).Ruptura: Si $T_{nodal} > T_{critico}$. (Conflicto abierto).4. VALIDACIÓN DE CALIBRACIÓN (BACKTESTING)Para el módulo de calibración (Capa 9), el error se minimiza comparando la curva simulada con la real, ajustando los coeficientes libres:$\alpha$ (Sensibilidad a Comunía)$\beta$ (Sensibilidad a Propósito)$\gamma$ (Eficacia del Escudo)$\lambda_h$ (Velocidad de olvido)$$MSE = \frac{1}{n} \sum (V_{sim} - V_{real})^2$$Especificación generada por El Marcante V2 - Basada estrictamente en Apéndice V10.1.
