---
layout: post
title:  "Machine learning: A formalism"
date:   2023-06-19
categories: ml formalism
hasmath: true
---


# Introduction


## Omniscient view


Observed data
\begin{equation}
	\mathcal{D} \subseteq \mathcal{X} \times \mathcal{Y}
\end{equation}

Task
\begin{equation}
	F : \mathcal{X} \rightarrow \mathcal{Y}
\end{equation}

\begin{equation}
	 F \in \mathcal{F}
 \end{equation}


Optimisation task
\begin{equation}
	\underset{F \in \mathcal{F}}{argmin}\ E [ L(F(x), y) ]\ \forall x, y \in \mathcal{D}
\end{equation}


## Reality

Observed data
\begin{equation}
	D \subseteq \mathcal{D}
\end{equation}

\begin{equation}
	D_{\text{train}} \subseteq D
\end{equation}

Test data
\begin{equation}
	D_{\text{test}} \subseteq D,\ s.t.\ D_{\text{test}} \cap D_{\text{train}} = \emptyset
\end{equation}

Learning approach
\begin{equation}
	A : \mathcal{X} \times \mathcal{Y} \rightarrow \mathcal{F}
\end{equation}

\begin{equation}
	A \in \mathcal{A}
\end{equation}

\begin{equation}
	F = A(D_{\text{train}})
\end{equation}

Optimisation task
\begin{equation}
	\underset{F \in \mathcal{F},\ F=A(D_{\text{train}})}{argmin}\ E [ L(M(x), y) ]\ \forall x, y \in \mathcal{D}_{\text{test}}
\end{equation}



## Sampling

\begin{equation}
	S : D \rightarrow (D_{\text{train}}, D_{\text{test}}),\ s.t.\ D_{\text{test}} \cap D_{\text{train}} = \emptyset
\end{equation}


## Learning approach


Feature extraction
\begin{equation}
	T : \mathcal{D} \rightarrow \mathcal{D^{T}}
\end{equation}

\begin{equation}
	D_{\text{train}}^{T} = T(D_{\text{train}})
\end{equation}
\begin{equation}
	D_{\text{test}}^{T} = T(D_{\text{test}})
\end{equation}

Feature selection


Learning







