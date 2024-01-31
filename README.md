# Gromov-Monge Barycenter Regularization for Counterfactual Regression

## 1 Abstract

As a promising individualized treatment effect (ITE) estimation method, counterfactual regression maps individuals' covariates to a latent space and predicts their counterfactual outcomes. 
However, the selection bias between control and treatment groups often imbalances the two groups' latent distributions and negatively impacts this method's performance.
In this study, we propose a novel Gromov-Monge barycenter regularization for counterfactual regression, suppressing selection bias while avoiding trivial latent distributions.
In principle, we formulate the regularization as a constrained Gromov-Monge (GM) barycenter problem, in which a transport map pushes the two groups' covariate distributions to the same latent distribution and the GM distance between each covariate distribution and the latent distribution is minimized.
We demonstrate that under mild assumptions, the Monge map associated with the GM distance is a feasible solution to the problem.
Accordingly, we reformulate the problem to an optimization-friendly format and optimize the transport map approximately as a neural network. 
Experiments on representative ITE estimation tasks show that applying our regularization outperforms state-of-the-art methods consistently under the counterfactual regression framework.

## 2 Quick Start

Choose a model (e.g., GMCFR) to run with the following command.

```
    python main.py --lr 0.01 --batchSize 32 --alpha 0.5 --beta 0.5 --lambda 0.1
```


## 3 Hyper-parameters search range

We tune hyper-parameters according to the following table.

| Hyper-parameter | Explain                | Range                                              |
| --------------- | ---------------------- | -------------------------------------------------- |
| lr              | learning rate          | \{0.00001, 0.0001, 0.001, 0.01, 0.1\} |
| batchSize      | batch size of each mini-batch | \{16, 32, 64, 128\} |
| dim_backbone    | the dimensions of representation  | \{32, 64, 128\}                         |
| dim_task    | the dimensions of prediction head | \{32, 64, 128\}                         |
| alpha              | weight of Gromov-Wasserstein distance               | \{0.1, 0.3, 0.5, 0.7, 0.9\}                         |
| beta       | weight of fused Gromov-Wasserstein distance            | \{0.1, 0.3, 0.5, 0.7, 0.9\}                              |
| lambda           | weight of OT regularization    | \{0.0001, 0.001, 0.01, 0.1, 1\}                               |


As different base models have different hyper-paramerters to tune, you can view the details in corresponding model files.
