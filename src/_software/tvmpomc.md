---
title: "t-VMPOMC.jl"
author: dhryniuk
header: 
    teaser: /assets/images/tvmpomc_logo.png
github: "dhryniuk/t-VMPOMC"
layout: single
classes: wide
excerpt: "A Julia package for solving many-body Lindblad master equations of dissipative spin chains via time-dependent variational Monte Carlo evolution of matrix product operators. Keywords: Open Quantum Systems, Dynamics, Variational Monte Carlo, Tensor Networks, Spins, Lattices, Long-range interactions"
---

{% if page.author %}
  {% assign author_id = page.author %}
  {% assign author = site.data.authors[author_id] %}
  <p class="page__meta" style="margin-top: 0.5em; margin-bottom: 2.0em; line-height: 1.2; color: grey; font-size: 1.0em; font-style: italic;">
    By {{ author.name }}
  </p>
{% endif %}

A Julia package for solving many-body Lindblad master equations of dissipative spin chains for the non-equilibrium dynamics via variational Monte Carlo optimization of matrix product operators.

Keywords: Open Quantum Systems, Dynamics, Variational Monte Carlo, Tensor Networks, Spins, Lattices, Long-range interactions

# Description:

This package is a Julia implementation of a time-dependent variational matrix product operator Monte Carlo method (t-VMPOMC). This methods simulates the non-equilibrium dynamics by means of time-dependent variational Monte Carlo applied to a matrix product operator (MPO) trial state for the many-body density operator. It is suitable for simulating finite, periodic, translationally-invariant, interacting spin chains in contact with an external Markovian environment, including spins with (multiple) long-range interactions. 

# Installation:

Simply clone the repository via
```
git clone https://github.com/dhryniuk/t-VMPOMC.git
```

# Example Problems:

[Dissipative Ising Model]({{ site.baseurl }}/problems/dissipative_ising)

# Further reading:
[Hryniuk, D. A.; Szymańska, M. H. Variational approach to open quantum systems with long-range competing interactions. arXiv:2510.01543 [quant-ph].](https://arxiv.org/abs/2510.01543)