# Stan Guidance

# Principles in prior design :<br/>

(1) Generative [1] <br/>
- Coherent with study/measurement design and prior beliefs <br/>
- Prior should interact well with the likelihood model, so the resulting posterior represents a meaningful data generating process <br/>
- Interaction between parameters: Avoid concentration of measure <br/>

(2) Predictive [1] <br/>
- Work well to predict future data given current data collected <br/>
- Useful to model selection or model averaging <br/>

(3) Computational efficiency <br/>
- Geometry: The resutling posterior is better to have a homogeneous manifold shape in the high-dimensional parameter space [2] <br/>
- Scale and shape of weakly informative prior [3]. Specific informative prior [5] <br/>
- Keep all sampling parameters in the same scale (e.g., Normal(0, 1)). <br/>
- Step size should not be too small, otherwise chain will move very slow. <br/>

(4) Avoid overfitting <br/>
- Think about if hierarchical prior is truly needed.

(5) Avoid uninformative flat prior if possible [4] <br/>
- Parameters might be truncated <br/>
- Uninformative flat prior is more likely to pickup parametric regions outside true parameter region, so might bias inference <br/>
- Prior predictive distribution and Bayes Factor might be useless with uninformative prior [1] <br/>

Refs: <br/>
[1] [The Prior Can Often Only Be Understood in the Context of the Likelihood](https://www.mdpi.com/1099-4300/19/10/555) <br/>
[2] [A Conceptual Introduction to Hamiltonian Monte Carlo](https://arxiv.org/abs/1701.02434) <br/>
[3] [How the Shape of a Weakly Informative Prior Affects Inferences](https://mc-stan.org/users/documentation/case-studies/weakly_informative_shapes.html) <br/>
[4] [Computational and statistical issues with uniform interval priors](https://statmodeling.stat.columbia.edu/2017/11/28/computational-statistical-issues-uniform-interval-priors/) <br/>
[5] [Prior Choice Recommendations](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations) <br/>

I'm still learning below refs. <br/>
[Prior Choice Recommendations](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations) <br/>
[Towards A Principled Bayesian Workflow](https://betanalpha.github.io/assets/case_studies/principled_bayesian_workflow.html) <br/>
[Penalising Model Component Complexity: A Principled, Practical Approach to Constructing Priors](https://projecteuclid.org/euclid.ss/1491465621) <br/>
[Moving beyond noninformative priors: why and how to choose
weakly informative priors in Bayesian analyses](https://onlinelibrary.wiley.com/doi/full/10.1111/oik.05985)
[Collinearity of Predictors in Regressions](https://mc-stan.org/docs/2_25/stan-users-guide/collinearity-section.html#collinearity.section)

Some comments

In complex models, however, it typically takes a significant amount of data for the likelihood to be able to identify a necessarily small region of parameter space. The more expensive and sparse the data and the more complex the likelihood, the more informative diffuse priors will be. If we want to make reasonable inferences in these models then we need more principled prior distributions that are actually coherent with our prior beliefs.

Weakly informative priors introduce scale information to regularize inferences. Scales are straightforward to reason about in applied problems, especially when units are carefully laid out, and they provide just enough information to regularize non-identified or weakly-identified likelihoods without strongly biasing the posterior away from reasonable parameter values. In order to construct weakly informative priors we need to first decompose our model into components, define default values, identify scales, then choose an explicit shape for our prior.


When the scales are well-chosen all weakly informative priors behave similarly, regularizing the posterior by penalizing extreme parameter values. But Cauchy prior is weaker than Gaussian prior, so the regulation by Cauchy prior is weaker than that of Gaussian prior, which may gives more probability mass on extreme values. Complex likelihood sensitive to extreme values might be peoblematic with Cauchy prior.


Q: What's "Stan actually works on the unconstrained space"?? A: It's described in the Chapter 10. Constraint Transforms in the [Reference Manual](https://mc-stan.org/docs/2_24/functions-reference-2_24.pdf)

# Within-chain parallelization

[reduce_sum tutorial](https://mc-stan.org/users/documentation/case-studies/reduce_sum_tutorial.html)


# leave-one-out (loo) cross-validation

[loo vignettes](https://github.com/stan-dev/loo/tree/master/vignettes)

[write loo in stan](https://mc-stan.org/loo/articles/loo2-with-rstan.html)


# R's C api

[R's internal C API](https://github.com/hadley/r-internals)

[Rstan on Windows](https://discourse.mc-stan.org/t/rstan-on-windows/16673)
