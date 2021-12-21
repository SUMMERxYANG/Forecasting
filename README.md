## Models Used

### ARIMA (Autoregressive Integrated Moving Average)

- Uses 3 parameters p, d, and q to parametrize the 3 major aspects of a time series - seasonality, trend, and noise.
- P is the number of autoregressive terms.
- D is the number of nonseasonal differences needed for stationarity. 
- Q is the number of lagged forecast errors.

### SARIMA (Seasonal ARIMA)

- Uses an additional parameter m in the parametrization to take into consideration the number of time steps for a single period

### SARIMAX

- SARIMA with an additional argument X, which allows exogenous variables to be added. 

## Understanding the Models:
- Time series are simply stochastic processes where the index set T in $\{X_t:t\in T\}$ is time.
- An **autoregressive process** of order 1 is an i.i.d. $N\left(0, \tau^{2}\right)$ process with $\left\{Z_{n}: n \in \mathbb{Z}\right\}$ and $X_{n}=\alpha X_{n-1}+Z_{n}$ where $X_{n-1}$ is independent of $Z_{n}$

### Stationarity:

- For $T \subset \mathbb R^{k}$, a stochastic process is said to be **weakly stationary** if 
  1. its mean function $\mu(t)$ is constant in t and 
  2. its autocovariance function $\sigma(s, t)=\kappa(s-t)$ for some $\kappa: \mathbb R^{k} \rightarrow \mathbb R^{1}$.
  
  **Note**: $\kappa$ is a positive semidefinite function, i.e. it must satisfy $\kappa(0) \geq 0, \kappa(t)=\kappa(-t)$, and $\displaystyle\sum_{i=1}^{n} \sum_{i=1}^{n} x_{i} x_{j} \kappa\left(t_{i}-t_{j}\right) \geq 0$ for all $\left\{t_{1}, \ldots, t_{n}\right\} \subset T$, $x=\left(x_{1}, \ldots, x_{n}\right)^{T} \in \mathbb R^{n}$
  
- A **strictly stationary** process has the property that $\left(X_{t_{1}+h}, \ldots, X_{t_{n}+h}\right) \sim\left(X_{t_{1}}, \ldots, X_{t_{n}}\right)$ where h is such that $\left\{t_{1}+h, \ldots, t_{n}+h\right\} \subset T$
  
  **Note**: A weakly stationary Gaussian process is always strictly stationary, since $\sigma\left(t_{i}+h, t_{j}+h\right)=\kappa\left(t_{i}-t_{j}\right)=\sigma\left(t_{i}, t_{j}\right)$ (similar to how covariance = 0 implies statistical independence with joint normality)

### Autocorrelation:

- Suppose $\left\{\left(t, X_{t}\right): t \in T\right\}$ is a stochastic process such that $E\left(X_{t}^{2}\right)<\infty$ for all $t \in T$. Then provided $\sigma(t, t)>0\ \forall t \in T$, the **autocorrelation function** $\rho: T \times T \rightarrow \mathbb R^{1}$ is defined as $\rho(s, t)=\displaystyle\frac{\sigma(s, t)} {\sqrt{\sigma(s, s)} \sqrt{\sigma(t, t)}}$
- In words, autocorrelation is the correlation of a signal with a delayed copy of itself as a function of delay (Wikipedia definition). Informally, it is the similarity between observations as a function of the time lag between them.