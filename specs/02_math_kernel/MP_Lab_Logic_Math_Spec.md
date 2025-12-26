**BLOQUE 2: Ecuaciones Maestras**
(Copia y pega esto justo debajo de la tabla en tu archivo)

```markdown
## 2. ECUACIONES MAESTRAS (EL KERNEL FÍSICO)

El backend debe implementar estas ecuaciones exactas para calcular el estado en cada paso de tiempo $t$.

### A. Ecuación General del Valor ($V_{10.1}$)

La fórmula integra Potencial, Propósito, Protección Ambiental y Memoria Histórica.

$$
V(t) = \left[ (A+S) \cdot M_{pe} \cdot e^{\alpha U(t)} \right] \cdot \underbrace{\frac{e^{\beta P}}{1 + \Sigma e^{-\gamma U(t)}}}_{\text{Factor Elevador & Escudo}} + \underbrace{\eta \int_{t_0}^{t} \Phi(\tau) d\tau}_{\text{Patrimonio (Memoria)}}
$$

* **Nota Dev:** El término integral se computa iterativamente como `PRN_new = PRN_old + (Phi_t * delta_t * eta)`.

### B. Dinámica de Flujo Instantáneo ($\Phi$)

El flujo de valor no es constante; depende de la Tensión Nodal y la Energía Relacional disponible.

$$
\Phi(t) = \frac{\text{sgn}(\Delta R(t)) \cdot ER(t)}{T_{nodal}(t) + \epsilon}
$$

Donde la **Energía Relacional Activa (**$ER$**)** está condicionada por la Habituación:

$$
ER(t) = k \cdot T_{nodal}(t) \cdot [1 - H(t)] \cdot e^{-\Delta t / \tau}
$$

* *Interpretación:* Si la Habituación $H(t)$ llega a 1 (aburrimiento total), la Energía $ER$ cae a 0, y el Flujo $\Phi$ se detiene.

### C. Función de Coherencia ($M_{pe}$)

Calculada trigonométricamente mediante producto punto de vectores normalizados.

$$
M_{pe} = \cos(\theta) = \frac{\vec{v}_{d} \cdot \vec{v}_{p}}{|\vec{v}_{d}| \cdot |\vec{v}_{p}|}
$$

* Rango:
  * $1.0$: Coherencia Total ($0^\circ$).
  * $0.0$: Irrelevancia ($90^\circ$).
  * $-1.0$: Incoherencia/Traición ($180^\circ$).

### D. Ley de Habituación ($H$)

Modelado del decaimiento del interés en ausencia de novedades (Momentos de la Verdad).

$$
H(t) = 1 - e^{-\lambda_h (t - t_{last\_MdV})}
$$

* **Trigger:** Un nuevo MdV resetea $t_{last\_MdV}$ al tiempo actual, haciendo que $H(t)$ caiga a 0 instantáneamente (reactivación).
