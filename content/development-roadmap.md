+++
title = 'Development Roadmap'
button = 'Roadmap'
weight = 10
toc = false
+++

A roadmap for agent-based model development.

## Model Parameter Rules

### Government

- The increase of 'Pure Expenditures' as a percentage is informed by an analysis of historic real-world expenditures. See *The Treasury view*: Godley & Lavoie, chapter 5, pp 147-165.
- Taxation: See the [taxation]({{< ref "/posts/taxation-themes" >}} "Taxation Themes") themes post.

### Central Bank

- The interest (base) rate set is a **lagged** reaction to the model velocity of bills. (CB rules may be further enhanced by a decision-tree classification analysis by real-world (BoE) interest rate decisions).
- Forward Guidance: The interest rate decision is made available to all agents in the next step.

### Producer(s)

- May employ multiple household agents.

### Household(s)

- Have bond price expectations that reflect Central Bank forward guidance.
