# disease_spread

##The Data

The dataset used by this model comes from a weighted-graph algorithm that dictates the evolution of the spread of a disease over a network of $n$ nodes. An edge between node $i$ and node $j$ has an assigned score of how likely it is for infected node $i$ to pass the disease to node $j$ or viceversa. The spread evolves over $T$ timesteps, where each timestep $t$ corresponds to a snapshot of the network after one day. There are $m$ different experiments of $T$ timesteps, in which at $t=0$ some few nodes are infected. Each node $i$ has an assigned number $p_i(t)\in[0,1]$ that represents the probability of having acquired the disease after $t$ timesteps. The scores of the edges do not evolve overtime and are the same for each experiment. What changes from experiment to experiment is what nodes are initially infected. In our dataset $m=4000$, $T=21$, and $n=100$.

##The Problem

The goal of the model is, given an initial state of the network with some infected nodes $\{ j\subseteq[n] : p_j(0)=1\}$, predict the evolution of the probabilities $\{p_i(t)\}_{i\neq j\in[n]}$ for $t=1,\dots, T$, without any knowledge of the scores, or any information about the network's connectivity. We would like to build a model that can predict the evolution of the probabilities $p_i(t)$ by hiding the causal factors of the evolution and showing to it only the actual evolutions. 
