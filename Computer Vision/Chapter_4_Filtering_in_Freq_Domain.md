# Fourier Series & Transform

* A function, expressed in fourier series/transform, can be reconstructed completely vie an inverse process with no loss of information.

**Allows us to work in the Fourier domain (generally called the frequency domain) and then return to the original domain of the function
without losing any information**

### Fourier Series
" Any **periodic** function can be expressed as the **sum of sines and/or cosines** of different frequencies, each **multiplied by a different coefficient** "

### Fourier Transform
Functions that are **not periodic** (but whose area under the curve is finite) can be expressed as the **integral** of sines and/or cosines **multiplied by a weighting function**

#### Computational Advantage (Filtering) in Frequency Domain

Image size (M x N), Kernel size (m x n)

**Non-Separable Kernel**

1. Spatial Domain:  $MNmn$
2. Frequency Domain: $2MN\log_2MN$

**Separable Kernel**
1. Spatial Domain: $MN(m+n)$
2. Frequency Domain: $2MN\log_2MN$

<br>

![comp_ad](img/comp_ad.png)

<br>

### Impulses
A unit impulse of a continuous variable t, located at
t = 0, and denoted $\delta(t)$, is defined as
<br>

$$
\delta(x) = \begin{cases}
    \infty &  t = 0 \\
    0 & t \neq 0
   \end{cases}
$$
where $\int_{-\infty}^{\infty} \delta(t)dt = 1$

#### Sifting

Yields the value of function f(t) at the location of the impulse
$$ \int_{-\infty}^{\infty} f(t)\delta(t-t_{0})dt = f(t_{0})$$

#### Impulse Train
Sum of infinitely many impulses $\Delta T$ units apart.
$$
s_{\Delta T}(t) = \sum_{k=-\infty}^{\infty} \delta(t-k\Delta T)
$$

![impulse](img/impulse.png)

<br>

### Fourier Transformation

**Continuous Variable**
$$
F(\mu) = \int_{-\infty}^{\infty} f(t)e^{-j2\pi \mu t}dt
$$

Inverse Fourier
$$
f(t) = \int_{-\infty}^{\infty} F(\mu)e^{j2\pi \mu t}d\mu
$$


E.g
![transform](img/transform.png)

Things to note:
1. Location of zeros are inversely proportional to the width, W.
2. Height of the lobes decreases as a function of distance from the origin
3. Function extends to infinity for both positive and negative values of $\mu$

### Convolution

$$
(f * h)(t) = \int_{-\infty}^{\infty}f(\tau)h(t-\tau)d\tau = (H \cdot F)(\mu)
$$

**Fourier Transform pair**
$$
(f \cdot h)(t) \leftrightarrow (H * F)(\mu)
$$

<br>

### Sampling
Required to convert continuous function into sequence of discrete values before being processed in a computer
$$
\bar{f}_k = f(t)s_{\Delta T}(t) = \sum_{n=-\infty}^{\infty} f(t)\delta(t-n\Delta T)
$$

<br>

![sampling](img/sampling.png)

$$
\bar F(\mu) = (F * S)(\mu) = \frac{1}{\Delta T}\sum_{n=-\infty}^{\infty}F(\mu - \frac{n}{\Delta T})
$$
Fourier transform $\bar F(\mu)$ of sampled function $\bar{f}(t)$ is an *infinite, periodic sequence of copies of the transform of the original continuous function*
- Continuous since it consists of copies of $F(\mu)$, which is continuous

<br>

#### Sampling Theorem

![under_over](img/under_over.png)

Extract from $\bar F(\mu)$ a single period that is equal to $F(\mu)$ is possible if:
$$
\frac{1}{\Delta T} > 2\mu_{max}
$$

Where sampling frequency exceeds twice the highest frequency of the content


**Recovering $F(\mu)$ from $\bar F(\mu)$** <br>


 ![recover](img/recovery.png)
 Function for Figure 4.8(b):
 $$
 H(\mu) = \begin{cases}
       \Delta T & -\mu_{max} \leq \mu \leq \mu_{max}\\
       0 & otherwise \\
    \end{cases}
  $$
where $H(\mu)$ is called *low-pass filter*

<br>

  With $F(\mu)$, recover $f(t)$ with
  $$
  f(t) = \int_{-\infty}^{\infty} F(\mu)e^{j2\pi \mu t}d\mu
  $$
  
