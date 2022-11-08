---
layout: post
title:  "A rough formalism for machine learning"
date:   2022-07-12 21:21:09 +0100
categories: ml
hasmath: true
---

$$\DeclareMathOperator*{\argmin}{argmain}$$


# Introduction


Observed data
\begin{equation}
	\mathcal{D} \subseteq \mathcal{X} \rightarrow \mathcal{Y}
\end{equation}

Task
\begin{equation}
	f : \mathcal{X} \rightarrow \mathcal{Y} \in F
\end{equation}

Learning approach
\begin{equation}
	F : \mathcal{X} \times \mathcal{Y} \rightarrow \mathcal{F}
\end{equation}

Optimisation task
\begin{equation}
	\argmin_{\beta} E [ L(f(x, \beta), y) ] \forall x, y \in \mathcal{D}
\end{equation}

Observed data
\begin{equation}
	D \subseteq \mathcal{D}
\end{equation}

Training data
\begin{equation}
	D_{\text{train}} \subseteq D
\end{equation}

Test data
\begin{equation}
	D_{\text{test}} \subseteq D
\end{equation}

Model learning
\begin{equation}
	f = F(D_{\text{train}})
\end{equation}

Optimisation task
\begin{equation}
	\argmin_{\beta} E [ L(f(x, \beta), y) ] \forall x, y \in \mathcal{D}_{\text{test}}
\end{equation}

asdf
