---
title: "Driven Dissipative Bose-Hubbard Model"
collection: problems
author: aferrier
show_author: true
toc_sidebar: true
layout: single
classes: wide
excerpt: "In this tutorial, we will study the behaviour of nonlinear bosonic lattice models with drive and decay."
---

{% if page.author %}
  {% assign author_id = page.author %}
  {% assign author = site.data.authors[author_id] %}
  <p class="page__meta" style="margin-top: 0.5em; margin-bottom: 2.0em; line-height: 1.2; color: grey; font-size: 1.0em; font-style: italic;">
    By {{ author.name }}
  </p>
{% endif %}

In this tutorial, we will use [Positive P]({{ site.baseurl }}/software/DDBHPP) to study the behaviour of some examples of driven dissipative Bose-Hubbard models.

# Recommended tutorials

[xmds2]({{ site.baseurl }}/tutorials/xmds)

# Introduction

In the most general form, without at this stage specifying the lattice geometry, the Hamiltonian for a driven Bose-Hubbard model can be written in the frame rotating with the driving frequency as

$$
\hat{H} = \sum_j \left( -\Delta\hat{a}^\dagger_j\hat{a}_j +\frac{U}{2}\hat{a}^\dagger_j\hat{a}^\dagger_j\hat{a}_j\hat{a}_j +F_j\hat{a}^\dagger_j + F_j^*\hat{a}_j \right) -\sum_{j,j'} \left(J_{j,j'}\hat{a}^\dagger_j\hat{a}_{j'} + J^*_{j,j'}\hat{a}^\dagger_{j'}\hat{a}_j \right) \, ,
$$

where $\Delta$ gives the detuning between the on-site energy and the driving frequency, $U$ the two-body interaction strength, $F_j$ the driving amplitude on each site $j$, and $J_{j,j'}$ the hopping between sites (typically $J_{j,j'} = J$ for connected sites and 0 otherwise).  Including the effects of dissipation to the external environment, the evolution of the system as described by the many-body density matrix $\hat{\rho}$ is given by a Markovian Lindblad master equation

\begin{equation} 
    \frac{\partial\hat{\rho}}{\partial t} = -i\left[\hat{H}, \hat{\rho}\right] + \sum_j\frac{\gamma}{2}\left(2\hat{a}_j\hat{\rho}\hat{a}^\dagger_j - \hat{a}^\dagger_j\hat{a}_j\hat{\rho} - \hat{\rho}\hat{a}^\dagger_j\hat{a}_j\right) \, , 
\end{equation}

where $\gamma$ is the dissipation rate (we set $\gamma=1$ in our units).

# Single Site

## Positive-P method

We will start by calculating the observables for the limiting case of the model of a single site nonlinear bosonic mode with consequently no hopping term.  Using [Positive-P]({{ site.baseurl }}/software/DDBHPP) simulations, we generate sets of stochastic trajectories for two complex variables $\alpha(t)$ and $\beta(t)$.  We will calculate the occupation $n$ and second-order correlation $g^{(2)}(0)$, which in the positive-P representation can be calculated by corresponding averages over trajectories: 

$$n = \langle \hat{a}^\dagger \hat{a} \rangle = \langle \alpha \beta \rangle_{PP}\, ,$$

$$g^{(2)}(0) = \frac{\langle \hat{a}^\dagger \hat{a}^\dagger \hat{a} \hat{a} \rangle}{\langle \hat{a}^\dagger \hat{a} \rangle^2} = \frac{\langle \alpha^2 \beta^2 \rangle_{PP}}{\langle \alpha \beta \rangle_{PP}^2}\, ,$$

where $\langle ... \rangle_{PP}$ is used to denote stochastic averages over the positive-P trajectories.  

To do this we will use the DDBH_1site_PP_template from our [DDBHPP]({{ site.baseurl }}/software/DDBHPP) repository.  Make a copy of this template directory to run the simulations in.  We will investigate initially for the default values of physical parameters provided there: $\Delta = 0$, $U = 0.1\gamma$, $F = \gamma$.  Use the bash command 
```bash
xmds2 DDBH_1site_PP.xmds
```
to compile the xmds script.  Then use 
```bash
./DDBH_1site_PP_runscript.sh
```
to generate trajectories.  When this is complete, we will calculate the desired observables using the Matlab library provided and the analysis.m script in the simulation directory.  Make sure the toolspath string in analysis.m gives the correct path to where you have the matlab_tools directory, and edit the list of scripts to run at the bottom of analysis.m:
```Matlab
%List of scripts to process data
DDBH1PP_tAv
DDBH1PP_dynamics
```
DDBH1PP_dynamics will generate the time evolution of the observables $n$ and $g^{(2)}(0)$ and their uncertainty calculated via a subensemble averaging procedure.  After loading the output file into Matlab, we can visualise the observables with error bars using the Matlab function:
```Matlab
figure
errorbar(t, n_t, err_n_t)
figure
errorbar(t, g2_t, err_g2_t)
```
which (after some adjustment of formatting to preference) should generate the following pair of figures:

![1site_example]({{ site.baseurl }}/assets/images/problems/









