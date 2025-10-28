# Phylogenetic dating analyses

Model and parameters:
* Tumor clade has a monophyletic constraint
* Root age calibrated at +/- 1 year of patient age
* FLC with two estimated strict clocks, one healthy clock, and one tumor clock
* Healthy clock prior Lognormal(meanlog=-5.5, sdlog=1.65), 95% interval = (0.00016, 0.10372)
* Tumor clock prior Lognormal(meanlog=-5.5, sdlog=1.65)
* Population size prior Lognormal(meanlog=2.35, sdlog=2.35), 95% interval = (0.10478, 1049.33862)
* Error priors allelic dropout delta ~ Beta(1, 2), 95% interval = (0.01258, 0.84189)
* Error priors sequencing/amplification error epsilon ~ Beta(1, 2)
* GT16 substitution model frequency prior pi ~ Dirichlet(3, 3, ..., 3)
* GT16 substitution model rates prior rates ~ Dirichlet(1, 2, 1, 1, 2, 1)

Additional operators:
* UpDownOperator with up = healthy clock, tumor clock and down = tree
* UpDownOperator with up = healthy clock, tumor clock and down = tree, popSizes
