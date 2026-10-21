# econ3916-lab09-ab-testing
# A/B Testing — Designing the Data-Generating Process

## Objective
I used a randomized job training experiment and a mobile game A/B test to show how the way data is generated decides whether a treatment effect can be trusted.

## Methodology
- I loaded the LaLonde NSW job training experiment (445 people: 185 trainees and 260 controls) and computed the experimental average treatment effect (ATE) on earnings.
- I simulated an observational comparison group to show selection bias, and split the gap as Observational ATE = True ATE + Selection Bias.
- I ran a permutation test with 9,999 shuffles to get a p-value for the ATE.
- I built a bootstrap BCa 95% confidence interval for the ATE.
- I ran a power analysis to find the power of this study and the sample size needed to detect three different dollar effects.
- I applied the same tests to the Cookie Cats mobile game A/B test (90,189 players, with the gate at level 30 or level 40), using Day-1 retention as the outcome.
- I wrote a sample-size function, `n_needed()`, checked its output against the power analysis, and used it to size a rerun of the Cookie Cats test.

## Key Findings
In the NSW experiment, trainees earned $1,794.34 more than controls. The permutation test gave p = 0.0046, and the 95% confidence interval ran from $575.18 to $3,262.37, so the effect is positive, though its exact size is uncertain.

When I replaced the randomized controls with the simulated comparison group, the estimated effect became −$14,784.45. The same program appeared to lower earnings. Using Observational ATE = True ATE + Selection Bias, the selection bias is −$16,578.79, more than nine times the size of the true effect. This shows how selection bias can reverse the sign of an estimate when treatment is not randomly assigned.

In Cookie Cats, players with the gate at level 30 had Day-1 retention 0.59 percentage points higher than players with the gate at level 40 (p = 0.0752). This difference is not statistically significant, so the test cannot rule out that there is no real difference. A rerun large enough to detect a 0.59 pp difference would need 111,192 players per group.
