# Stan Guidance

# Prior

[Computational and statistical issues with uniform interval priors](https://statmodeling.stat.columbia.edu/2017/11/28/computational-statistical-issues-uniform-interval-priors/)

[Prior Choice Recommendations](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations)

[Towards A Principled Bayesian Workflow](https://betanalpha.github.io/assets/case_studies/principled_bayesian_workflow.html)

[How the Shape of a Weakly Informative Prior Affects Inferences](https://mc-stan.org/users/documentation/case-studies/weakly_informative_shapes.html)

Key criteria to consider (guess):<br/>
(1) Geometry of posterior in high-dimensional space should be homogeneous. It is good to keep all sampling parameters in the same scale (e.g., Normal(0, 1)).
(2)


In complex models, however, it typically takes a significant amount of data for the likelihood to be able to identify a necessarily small region of parameter space. The more expensive and sparse the data and the more complex the likelihood, the more informative diffuse priors will be. If we want to make reasonable inferences in these models then we need more principled prior distributions that are actually coherent with our prior beliefs.

Weakly informative priors introduce scale information to regularize inferences. Scales are straightforward to reason about in applied problems, especially when units are carefully laid out, and they provide just enough information to regularize non-identified or weakly-identified likelihoods without strongly biasing the posterior away from reasonable parameter values. In order to construct weakly informative priors we need to first decompose our model into components, define default values, identify scales, then choose an explicit shape for our prior.


When the scales are well-chosen all weakly informative priors behave similarly, regularizing the posterior by penalizing extreme parameter values. But Cauchy prior is weaker than Gaussian prior, so the regulation by Cauchy prior is weaker than that of Gaussian prior, which may gives more probability mass on extreme values. Complex likelihood sensitive to extreme values might be peoblematic with Cauchy prior.


Q: What's "Stan actually works on the unconstrained space"?? A: It's described in the Chapter 10. Constraint Transforms in the [Reference Manual](https://mc-stan.org/docs/2_24/functions-reference-2_24.pdf)

# leave-one-out (loo) cross-validation

[loo vignettes](https://github.com/stan-dev/loo/tree/master/vignettes)

[write loo in stan](https://mc-stan.org/loo/articles/loo2-with-rstan.html)


# R's C api

[R's internal C API](https://github.com/hadley/r-internals)

[Rstan on Windows](https://discourse.mc-stan.org/t/rstan-on-windows/16673)
