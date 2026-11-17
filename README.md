# Semi-Supervised Learning Lab

An interactive study guide for §19.3–19.3.5 of Kevin P. Murphy, *Probabilistic Machine Learning: An Introduction*
(semi-supervised learning, self-training and pseudo-labeling, entropy minimization, the cluster assumption, input-output mutual information, co-training, tri-training, label propagation on graphs and consistency regularization).

**Live:** https://isaackrallison.github.io/semi-supervised-learning/

Every section has an **Explain it** box at four levels (Kid, High school, Undergrad, Grad / MLE), switchable globally from the top bar.

- **19.3 Semi-supervised learning:** Fig. 19.8 with a classifier. Pick 1–10 labels per class on two-moons data, compare a supervised RBF logistic regression trained on the labels alone with label propagation over the unlabeled pool, and see accuracy vs number of labels averaged over 12 random draws.
- **19.3.1 Self-training:** offline pseudo-labeling one round at a time with a confidence threshold τ. Draw A goes from 80.5% to 99.8% test accuracy; Draw B shows confirmation bias (80.8% → 70.5%, 83 wrong pseudo-labels); τ = 0.5 just re-learns the first guess. Click any point to label or unlabel it.
- **19.3.2 Entropy minimization:** Fig. 19.9 live. Entropy, self-training (−max log p) and sharpened losses vs the logit, with a temperature slider and the targets q each loss trains toward.
- **19.3.2.1 The cluster assumption:** Fig. 19.10 on a linear classifier with draggable labeled points. Gradient descent on labeled CE + λᵤ·mean entropy (+ λ_b·balance term), a hover bar plot of each point's probabilities, and a profile of unlabeled loss vs boundary position that shows the valley in the gap and the degenerate "everything one class" trap (Draw B).
- **19.3.2.2 Mutual information:** nine 3-class predictions with confidence and "pull toward A" sliders; E[H(p)], H(p̄) and I = H(p̄) − E[H(p)], with maps of the entropy-minimization and MI losses over both sliders.
- **19.3.3 Co-training and tri-training:** two linked views of the same points; models hand confident labels to each other (58% → 87% for view 1, 93% combined), and stall with correlated views (~55%). Then three bootstrap RBF models with two-agree-teach-the-third (vote 79% → 98%) until they all agree.
- **19.3.4 Label propagation:** kNN graph with adjustable k and σ on moons, noisy moons and circles; step Y ← TY / renormalize / clamp, jump to the closed form (I − T̄_UU)⁻¹ T̄_UL Y_L, watch convergence on a log scale, click nodes to (mis)label them, and fit an inductive classifier to the propagated labels.
- **19.3.5 Consistency regularization:** Eq. 19.27 trained live on the two moons with Gaussian-noise or VAT perturbations (Eqs. 19.28–19.29, exact input gradients), squared error or KL, λ ramp-up, and arrows showing x → x′. Both draws reach ~99.5% (including Draw B, where self-training failed); noise σ = 0.8 crosses into the other moon and drops accuracy to ~56%. Plus Fig. 19.11: squared error vs KL (and their gradients) against the perturbed logit.
- A 57-question quiz tagged by level and a cheat sheet.

Single self-contained `index.html`, no build step. Loads Google Fonts and MathJax from cdnjs. All data are synthetic and generated in the page from fixed seeds. Every model, graph and fixed point is computed live in the browser.
