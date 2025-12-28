# bayesian-network-for-car-diagnostics
R1 — Bayesian Network Construction and Visualization
You correctly defined a directed acyclic graph (DAG) representing a car diagnosis Bayesian Network with:
Root causes:
ba (Battery)
ab (Alternator Belt)
fb (Fan Belt)
Intermediate faults:
bd (Battery Dead)
nc (No Charge)
bf (Battery Failure)
Observed symptoms:
l (Lights)
gg (Gas Gauge)
dl (Dashboard Lights)
The CPTs are encoded directly as node attributes, and the structure is consistent with causal reasoning in automotive diagnostics.
Both visualization approaches (graphviz_layout and spring_layout) are valid; the Graphviz layout is more appropriate for hierarchical Bayesian Networks.
R2 — 
P
(
+
f
b
∣
−
l
,
−
g
g
)
P(+fb∣−l,−gg)
Method 1 (Recursive marginalization)
You enumerated all free variables:
ba, ab, bd, bf, nc
You correctly summed over all joint assignments consistent with:
fb = y, l = n, gg = n
Method 2 (Explicit nested loops)
You independently recomputed the same marginal probability using full joint factorization.
Result (both methods match):
P
(
+
f
b
∣
−
l
,
−
g
g
)
=
0.165924
P(+fb∣−l,−gg)=0.165924
This confirms:
Correct CPT indexing
Correct parent–child dependency handling
Correct marginalization logic
R3 — 
P
(
+
a
b
∣
−
l
,
−
g
g
)
P(+ab∣−l,−gg)
Again, you correctly:
Fixed ab = y, l = n, gg = n
Marginalized over remaining variables
Result:
P
(
+
a
b
∣
−
l
,
−
g
g
)
=
0.050446
P(+ab∣−l,−gg)=0.050446
This value is significantly lower than R2, which is diagnostically meaningful.
R4 — 
P
(
−
g
g
∣
+
b
a
,
−
a
b
,
−
f
b
)
P(−gg∣+ba,−ab,−fb)
Here you evaluated the probability of gas gauge working given:
Battery OK
Alternator not broken
Fan belt not broken
You marginalised over:
bd, bf, nc, l
Result:
P
(
−
g
g
∣
+
b
a
,
−
a
b
,
−
f
b
)
=
0.0762363
P(−gg∣+ba,−ab,−fb)=0.0762363
This relatively low probability indicates that even when the major components are fine, other dependencies (battery failure chain) still affect the gas gauge.
R5 — Diagnostic Conclusion (Correct)
Your final inference is logically and probabilistically correct:
Since
P
(
+
f
b
∣
−
l
,
−
g
g
)
=
0.165924
P(+fb∣−l,−gg)=0.165924
is greater than
P
(
+
a
b
∣
−
l
,
−
g
g
)
=
0.050446
,
P(+ab∣−l,−gg)=0.050446,
the fan belt is more likely than the alternator belt to be the root cause of the observed symptoms.
Interpretation:
The Bayesian Network correctly propagates uncertainty.
The fan belt has a stronger causal influence on both lights and gas gauge failure under the given evidence.
Your numerical conclusion is fully supported by the model.
