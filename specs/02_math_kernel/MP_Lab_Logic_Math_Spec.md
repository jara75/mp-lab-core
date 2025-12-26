\documentclass[12pt, a4paper]{article}

% --- PAQUETES DE IDIOMA Y CODIFICACIÓN ---
\usepackage[spanish, es-tabla]{babel} % Español y "Tabla" en lugar de "Cuadro"
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}

% --- PAQUETES MATEMÁTICOS Y DE FORMATO ---
\usepackage{amsmath, amssymb, amsfonts} % Ecuaciones y símbolos avanzados
\usepackage{geometry} % Márgenes
\usepackage{booktabs} % Tablas profesionales
\usepackage{graphicx} % Imágenes (si se necesitan)
\usepackage{hyperref} % Enlaces y metadatos PDF
\usepackage{parskip}  % Espaciado entre párrafos sin sangría

% --- CONFIGURACIÓN DE GEOMETRÍA ---
\geometry{
    top=2.5cm,
    bottom=2.5cm,
    left=2.5cm,
    right=2.5cm
}

% --- METADATOS DEL DOCUMENTO ---
\title{\textbf{MP-LAB V1.0} \\ \large Especificación de Lógica y Matemática}
\author{Centro de Pensamiento Marcaje Personizante (MP)}
\date{\today \\ \small Versión del Kernel: V10.1}

\begin{document}

\maketitle
\thispagestyle{empty}

\begin{abstract}
    \noindent \textbf{Propósito:} Definir las reglas de negocio, el diccionario de variables y las ecuaciones diferenciales que gobiernan la simulación estocástica de MP-Lab, basándose estrictamente en el Apéndice Académico V10.1 (Dinámica de Vorticidad Relacional).
\end{abstract}

\vspace{0.5cm}

\section{Diccionario de Variables}
El siguiente cuadro define el lenguaje común entre la física del modelo y la implementación en el backend.

\begin{center}
\resizebox{\textwidth}{!}{% Ajustar tabla al ancho si es necesario
\begin{tabular}{l l l l}
\toprule
\textbf{Símbolo} & \textbf{Variable} & \textbf{Naturaleza} & \textbf{Definición Operativa / Psicológica} \\
\midrule
$A$ & Atributos del producto & Material & Valor intrínseco tangible y funcional. \\
$S$ & Oferta de servicio & Material & Condiciones de acceso y desempeño. \\
$M_{pe}$ & Coherencia & Relacional & Alineación identitaria (cálculo trigonométrico). \\
$U(t)$ & Comunía & Clima & Habitabilidad y escudo contra interferencia. \\
$P$ & Propósito & Vectorial & Fuerza negentrópica activa (sentido). \\
$\Sigma$ & Interferencia Externa & Entrópica & Ruido, competencia y saturación ambiental. \\
$V(t)$ & Valor Personizante & Sistémica & Nivel energético global del sistema. \\
$\Phi(t)$ & Flujo Relacional & Dinámica & Intercambio instantáneo de valor. \\
$PRN(t)$ & Patrimonio Relacional & Acumulativa & Capital histórico (Brand Equity). \\
$H(t)$ & Habituación & Entrópica & Memoria entrópica por monotonía. \\
$R_{MP}$ & Resistencia Activa & Identidad & Fuerza de coherencia interna y voluntad. \\
$R_{P}$ & Resistencia Pasiva & Entropía & Inercia del mercado, cinismo, escepticismo. \\
$\Delta R$ & Diferencial de Resistencia & Motor & Generador de tensión nodal ($R_{MP} - R_{P}$). \\
$\eta$ & Conversión Patrimonial & Empírico & Coeficiente de acoplamiento financiero. \\
\bottomrule
\end{tabular}
}
\end{center}

\section{Ecuaciones Maestras}
El sistema de simulación debe implementar estas ecuaciones exactas para calcular el estado del sistema en cada paso de tiempo $t$.

\subsection{Ecuación General del Valor ($V_{10.1}$)}
La fórmula integra Potencial, Propósito, Protección Ambiental y Memoria Histórica.

\begin{equation}
    V(t) = \left[ (A+S) \cdot M_{pe} \cdot e^{\alpha U(t)} \right] \cdot \underbrace{\frac{e^{\beta P}}{1 + \Sigma e^{-\gamma U(t)}}}_{\text{Factor Elevador \& Escudo}} + \underbrace{\eta \int_{t_0}^{t} \Phi(\tau) \, d\tau}_{\text{Patrimonio (Memoria)}}
\end{equation}

\textbf{Nota de Implementación:} El término integral debe computarse iterativamente en la simulación discreta:
\[ PRN_{new} = PRN_{old} + (\Phi_t \cdot \Delta t \cdot \eta) \]

\subsection{Dinámica de Flujo Instantáneo ($\Phi$)}
El flujo depende de la dirección de la Tensión Nodal y de la Energía Relacional activa.

\begin{equation}
    \Phi(t) = \frac{\text{sgn}(\Delta R(t)) \cdot ER(t)}{T_{nodal}(t) + \epsilon}
\end{equation}

\subsection{Energía Relacional Activa ($ER$)}
La energía disponible para realizar trabajo relacional decae con la habituación.

\begin{equation}
    ER(t) = k \cdot T_{nodal}(t) \cdot [1 - H(t)] \cdot e^{-\Delta t / \tau}
\end{equation}

\textit{Interpretación Física:} Si $H(t) \to 1$ (aburrimiento total), entonces $ER(t) \to 0$ y el sistema deja de transferir valor, independientemente de sus atributos ($A+S$).

\subsection{Función de Coherencia ($M_{pe}$)}
Calculada como el coseno del ángulo entre el vector de identidad declarada y el vector de comportamiento percibido.

\begin{equation}
    M_{pe} = \cos(\theta) = \frac{\vec{v}_{d} \cdot \vec{v}_{p}}{|\vec{v}_{d}| \cdot |\vec{v}_{p}|}
\end{equation}

\subsection{Ley de Habituación ($H$)}
Modelado del decaimiento exponencial del interés en ausencia de novedades (Momentos de la Verdad).

\begin{equation}
    H(t) = 1 - e^{-\lambda_h (t - t_{last\_MdV})}
\end{equation}

\textbf{Trigger de Reactivación:} Un Momento de la Verdad (MdV) significativo resetea el contador:
\[ H(t_{MdV}) = 0 \]

\section{Motor de Transición Markoviano}
Las probabilidades de transición en la matriz estocástica dependen de la Energía Relacional ($ER$) y la distancia topológica entre estados.

\begin{equation}
    P_{i \to j} \propto \exp\left( \frac{\Delta R(t) \cdot \kappa_{ij}}{\text{dist}(i,j)^\gamma} \right)
\end{equation}

\textbf{Regla de Negocio (Efecto Túnel):} Si $ER(t) > E_{critico}$, se habilitan transiciones no-lineales (ej. saltos directos de "Indiferente" a "Fiel" sin pasar por "Cliente").

\section{Condiciones de Estabilidad (Watchdog)}
El sistema debe alertar si la simulación entra en zonas topológicamente inestables:
\begin{itemize}
    \item \textbf{Muerte Térmica:} $T_{nodal} \approx 0$ (Sistema estático, sin flujo).
    \item \textbf{Ruptura del Sistema:} $T_{nodal} > T_{critico}$ (Conflicto abierto o deserción masiva).
\end{itemize}

\section{Validación de Calibración (Backtesting)}
El sistema ajusta sus parámetros libres minimizando el error cuadrático medio (MSE) entre la trayectoria histórica real y la simulada.

\begin{equation}
    MSE = \frac{1}{n} \sum_{i=1}^{n} (V_{sim}(t_i) - V_{real}(t_i))^2
\end{equation}

\textbf{Parámetros de Ajuste (Tuning):}
\[ \alpha, \beta, \gamma, \lambda_h, \lambda_U, \eta \]

\vfill
\hrule
\vspace{0.3cm}
\centering
\small \textit{Especificación generada por El Marcante V2 — Autoridad Técnica del MP.} \\
\textit{Documento confidencial para uso exclusivo de Google Antigravity.}

\end{document}
