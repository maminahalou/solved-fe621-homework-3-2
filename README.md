Download Link: https://assignmentchef.com/product/solved-fe621-homework-3-2
<br>
<h1>1         Quadratic Volatility Model</h1>

Consider a drift-less, time-homogeneous stochastic process <em>X<sub>t</sub></em>, <em>t </em>≥ 0, i.e.

<em>dX<sub>t </sub></em>= <em>σ</em>(<em>X<sub>t</sub></em>)<em>dW<sub>t </sub></em>with <em>X</em><sub>0 </sub>= <em>x</em><sub>0</sub>

and assume that

<em>σ</em>(<em>x</em>) = <em>αx</em><sup>2 </sup>+ <em>βx </em>+ <em>γ.</em>

In this case, the transition probability density for <em>X<sub>t</sub></em>, denoted by <em>p</em>(<em>t,x</em>|<em>X</em><sub>0</sub>0), satisfies the PDE:

(1)

with the initial condition

<em>p</em>(<em>t </em>= 0<em>,s </em>| <em>s</em><sub>0</sub>) = <em>δ</em>(<em>s </em>− <em>s</em><sub>0</sub>)

Here, <em>δ</em>(<em>x</em>) is the delta function which is equal to 1 at <em>x </em>= 0 and zero elsewhere. It can be shown that, by using the following transformation in the space domain:

the transformed PDE becomes analytically solvable, see [3]. In the transformed space <em>s</em>(<em>x</em>), we obtain

where. It turns out that <em>P</em>(<em>t,s </em>| <em>s</em><sub>0</sub>) is explicitly invertible. The inverted solution is:

!

Furthermore, the price of an European call option with zero interest rate may be obtained in explicit form using this transition density:

where, and Φ(·) is the cumulative distribution function of a standard normal. Please answer the following questions.

<ul>

 <li>Let <em>t </em>= <em>t</em><sub>1 </sub>be fixed. Compute and plot in 3 dimensions the surface <em>p</em>(<em>t,x </em>| <em>x</em><sub>0</sub>), for some parameters of your choice. To show the dynamics of this surface, plot the same surface for a different time <em>t</em><sub>2</sub>. Does this surface seem appropriate? Please comment.</li>

 <li>(Bonus) Check numerically, using finite difference approximations, that the transition probability density satisfies the initial PDE. (1)</li>

 <li>Pick a strike and a maturity value. Compute the price of an European call option assuming that the prices dynamics is described by a quadratic volatility process (use the formula above). Compare your results with the Black-Scholes price of the same option.</li>

</ul>

<h1>2         Fast Fourier Transform</h1>

In the paper [2], the authors show how the Fast Fourier Transform (FFT) may be used to value options when the characteristic function is known analytically. As it turns out, this method is highly efficient from the numerical point of view. Please read the paper [2], and pay special attention to sections 2, 3.1, and 4.

Let <em>C<sub>T</sub></em>(<em>k</em>) be the desired value of a <em>T</em>-maturity call option with strike <em>K</em>, where we denote <em>k </em>:= <em>ln</em>(<em>K</em>). The authors proved that (see equation (5) in the above citation):

(4)

where <em>i </em>is the imaginary number, and <em>ψ<sub>T</sub></em>(<em>v</em>) is given in equation (6). Note that <em>ψ<sub>T</sub></em>(<em>v</em>) is given in terms of the characteristic function of the log price, i.e., Φ<em><sub>T</sub></em>(<em>u</em>) = E[<em>e<sup>ius</sup></em><em><sup>T</sup></em>], <em>s<sub>T </sub></em>:= ln(<em>S<sub>T</sub></em>).

To implement the formula in (4), one needs to compute or approximate the integral. This can be accomplished using the FFT method, please see section 4 and equation (24).

Consider now the Black-Scholes model, for which the log price is normally distributed. Implement the FFT transform method for the Black-Scholes model, and price an European call option with suitably chosen parameters (you may use parameters from the previous assignments). Compare your result with the Black-Scholes formula. You can use any package or library to do this.

<h1>3         (BONUS) SABR parameter estimation</h1>

From Fabrice Douglas Rouah’s paper [1], the author shows how to estimate the parameters in a SABR model. In this question, you are required to use swaption data from the file “2017 2 15 mid.xlsx” to estimate SABR parameters. Here is the detailed information of the data structure in that file: Each column represents the maturity of a swaption contract (exercise time). Specifically, 1Yr; 2Yr;<em>…</em>; 30Yr represent the maturity T in equation (3) in the Rouah paper. In this data set, all swaptions are European Call options with the underlying a swap. Each row, which is marked with 1Mo, 2Mo, … , 30Yr represent the maturity of the underlying swap. You have the option to enter into this swap at the exercising time of the swaption (T). “Vol” is at-the-money volatility for each swaption contract and “strike” is the strike price K for each of the contracts. NOTE all the contracts are AT-THE-MONEY contracts (i.e. forward rate equals strike). Pick one maturity (1Yr, 2Yr, …, 30Yr) you are interested in (one column) and answer the following questions.

<ol>

 <li>Assume <em>β </em>= 0<em>.</em>5, implement equation (5) to estimate parameters <em>α</em>, <em>ρ </em>and <em>ν</em>. To solve this equation, you can use any standard optimization method such as Newton-Raphson method. For this question, you could use any available package to solve it.</li>

 <li>Set <em>β </em>= 0<em>.</em>7 and 0<em>.</em>4, and repeat part 1. That is, estimate the corresponding <em>α</em>, <em>ρ </em>and <em>ν </em></li>

 <li>Compare the parameters you obtained based on different <em>β </em>choice values. What do you observe? Write a paragraph to explain your observations.</li>

 <li>Using the maximum (minimum) of the function you optimized, tell us which model would give you best estimation.</li>

 <li>Using the best parameter values do the following: Select another contract you have not used in the previous question (a different column) and treat it as a benchmark. That is, calculate at-the-money volatility using the parameters you obtained and compare the numbers you see in the benchmark column. What do you observe? Please describe.</li>

</ol>