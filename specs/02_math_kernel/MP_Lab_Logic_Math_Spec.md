% MP-LAB — ESPECIFICACIÓN DE LÓGICA Y MATEMÁTICA (V10.1)
% Listo para Overleaf — Archivo standalone

\documentclass[12pt]{article}
\usepackage[spanish]{babel}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{amsmath, amssymb}
\usepackage{geometry}
\usepackage{booktabs}
\geometry{margin=2.5cm}

\title{MP-LAB V1.0 \\ \large Especificación de Lógica y Matemática}
\date{}

\begin{document}
\maketitle

\section*{Propósito}
Definir las reglas de negocio y ecuaciones que gobiernan la simulación MP-Lab según el Apéndice Académico V10.1 (Dinámica de Vorticidad Relacional).

---

\section{Diccionario de Variables}

\begin{center}
\begin{tabular}{llll}
\toprule
Símbolo & Variable & Naturaleza & Definición Operativa \\ 
\midrule
$A$ & Atributos del producto & Material & Valor intrínseco tangible y funcional. \\
$S$ & Oferta de servicio & Material & Condiciones de acceso y desempeño. \\
$M_{pe}$ & Coherencia & Relacional & Alineación identitaria (cálculo trigonométrico). \\
$U(t)$ & Comunía & Clima & Habitabilidad y escudo contra interferencia. \\
$P$ & Propósito & Vectorial & Fuerza negentrópica activa (sentido). \\
$\Sigma$ & Interferencia Externa & Entrópica & Ruido, competencia y saturación. \\
$V(t)$ & Valor Personizante & Sistémica & Nivel energético global del sistema. \\
$\Phi(t)$ & Flujo Relacional & Dinámica & Intercambio instantáneo de valor. \\
$PRN(t)$ & Patrimonio Relacional & Acumulativa & Memoria histórica (Brand Equity). \\
$H(t)$ & Habituación & Entrópica & Memoria entrópica por monotonía (aburrimiento). \\
$R_{MP}$ & Resistencia Activa & Identidad & Voluntad de coherencia interna. \\
$R_{P}$ & Resistencia Pasiva & Entropía & Inercia del mercado, cinismo, escepticismo. \\
$\Delta R$ & Diferencial de Resistencia & Motor & Generador de tensión nodal ($R_{MP}-R_P$). \\
$\eta$ & Conversión Patrimonial & Empírico & Coeficiente de acoplamiento financiero. \\
\bottomrule
\end{tabular}
\end{center}

---

\section{Ecuaciones Maestras}

\subsection{Ecuación General del Valor ($V_{10.1}$)}
\begin{equation}
V(t) = \left[(A+S)M_{pe}e^{\alpha U(t)}\right] \cdot \frac{e^{\beta P}}{1 + \Sigma e^{-\gamma U(t)}} + \eta \int_{t_0}^{t} \Phi(\tau)\,d\tau
\end{equation}

Nota de implementación:
\begin{equation}
PRN_{new} = PRN_{old} + (\Phi_t \cdot \Delta t \cdot \eta)
\end{equation}

\subsection{Flujo Instantáneo ($\Phi$)}
\begin{equation}
\Phi(t) = \frac{\text{sgn}(\Delta R(t))\cdot ER(t)}{T_{nodal}(t) + \epsilon}
\end{equation}

\subsection{Energía Relacional}
\begin{equation}
ER(t) = k\,T_{nodal}(t)\,[1 - H(t)]\,e^{-\Delta t / \tau}
\end{equation}

Interpretación:
Si $H(t)\rightarrow 1$, entonces $ER(t)\rightarrow 0$ y el sistema deja de transferir valor.

\subsection{Coherencia ($M_{pe}$)}
\begin{equation}
M_{pe} = \cos(\theta) = \frac{\vec{v}_{d} \cdot \vec{v}_{p}}{\|\vec{v}_{d}\|\,\|\vec{v}_{p}\|}
\end{equation}

\subsection{Habituación ($H$)}
\begin{equation}
H(t) = 1 - e^{-\lambda_h (t - t_{lastMdV})}
\end{equation}

Un Momento de la Verdad (MdV) resetea:
\begin{equation}
H(t_{MdV}) = 0
\end{equation}

---

\section{Motor de Transición Markoviano}

\begin{equation}
P_{i \to j} \propto \exp\left( \frac{\Delta R(t) \cdot \kappa_{ij}}{\text{dist}(i,j)^{\gamma}} \right)
\end{equation}

Regla de negocio:
Si $ER(t) > E_{critico}$ se permiten saltos no lineales ("Indiferente" → "Fiel").

---

\section{Condiciones de Estabilidad}

\begin{itemize}
  \item Muerte térmica: $T_{nodal} \approx 0$
  \item Ruptura: $T_{nodal} > T_{critico}$
\end{itemize}

---

\section{Validación de Calibración}

El sistema debe ajustar parámetros para minimizar error entre trayectoria real y simulada.

\begin{equation}
MSE = \frac{1}{n}\sum (V_{sim} - V_{real})^2
\end{equation}

Parámetros ajustables:
\begin{equation}
\alpha,\beta,\gamma,\lambda_h,\lambda_U,\lambda_{PRN},\eta
\end{equation}

---

\vfill
\begin{center}
\textit{Especificación generada por El Marcante V2 — basada estrictamente en Apéndice Académico V10.1}
\end{center}

\end{document}
