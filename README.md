# CS-370

**Current/Emerging Trends in Computer Science**

Michael Foster | Southern New Hampshire University

## Pirate Intelligent Agent

This project applies reinforcement learning and neural networks to a treasure hunt game. The pirate agent learns to navigate an 8 by 8 maze by choosing actions, receiving rewards, and improving its estimates of future rewards through deep Q-learning.

### Portfolio files

- [Michael_Foster_ProjectTwo.ipynb](Michael_Foster_ProjectTwo.ipynb): My completed pirate intelligent agent notebook.
- [TreasureMaze.py](TreasureMaze.py): The supplied maze environment, movement rules, and rewards.
- [GameExperience.py](GameExperience.py): The supplied experience replay and training target support.
- [requirements.txt](requirements.txt): Python dependencies for the project.

## Project reflection

### What code was I given, and what code did I create myself?

I was given the notebook framework, the maze layout, and the `TreasureMaze` and `GameExperience` classes. The starter notebook also included the neural network architecture, training helper, visualization functions, and functions for playing a game and checking completion. These components provided the environment and learning tools, while the main training loop in `qtrain()` was left for me to complete.

My contribution was turning that training skeleton into a working learning loop. I reset the maze at a random free cell, selected actions through exploration or the highest predicted Q-value, and recorded each action's state, reward, next state, and completion flag. I connected replay batches to the training helper, updated the target network periodically, and tracked wins and losses. The completed `qtrain()` function in the notebook connects these components into the agent's training process. It uses a 32-game history window and requires both a full window of wins and a successful completion check before stopping early.

### What do computer scientists do, and why does it matter?

Computer scientists translate problems into representations that computers can work with, design algorithms, and evaluate whether the results meet people's needs. In this project, that meant representing the maze as numerical state information and learning which actions could lead to the treasure. This work matters because the same problem-solving skills support systems that help people make decisions, recognize patterns, and automate tasks. Choosing a suitable method and explaining its limitations are part of that responsibility. A learned maze policy demonstrates reinforcement learning, while a known map could also be approached with a graph search algorithm.

### How do I approach a problem as a computer scientist?

I begin by defining the goal, identifying constraints, and deciding what evidence would demonstrate success. For the pirate agent, that means reaching the treasure within the maze's movement rules and reward limits. I break the problem into environment behavior, action selection, experience storage, network training, and evaluation. Understanding how `TreasureMaze`, `GameExperience`, and the notebook interact helps me reason about each part before connecting the full training process.

I also evaluate behavior against the original goal. The notebook combines a recent win rate with `completion_check()`, which tests the agent from eligible free starting cells in the supplied maze. This provides a broader check than watching one successful game. Success on the supplied maze still does not establish a shortest route or show that the agent will succeed on an unfamiliar maze. This project helped me connect reinforcement learning concepts such as exploration, experience replay, and target networks to an implementation I can inspect and evaluate.

### What are my ethical responsibilities to the end user and the organization?

I am responsible for explaining what a system does, how it was evaluated, and where its limitations remain. In this project, that includes crediting the supplied code and describing my own contribution accurately. The maze's rewards encourage reaching the treasure and discourage unnecessary movement, illustrating how an optimization goal influences an agent's behavior. I need to consider whether the objective I give a system reflects the outcome its users actually need.

For end users, I should protect personal information, explain limitations clearly, and provide meaningful control where automated decisions affect them. For an organization, I should produce maintainable code, document assumptions, evaluate reliability and unequal outcomes, and communicate risks honestly. In the pirate project, that includes distinguishing a recent win rate from broader evidence of reliable behavior and acknowledging that the reward design influences what the agent learns. A system's success metric needs to reflect the intended outcome for its users.

## Running the notebook

From the repository directory, install the dependencies and launch JupyterLab:

```bash
python -m pip install -r requirements.txt jupyterlab
python -m jupyterlab Michael_Foster_ProjectTwo.ipynb
```

Keep both Python helper files in the same directory as the notebook. Run the cells in order from a fresh kernel to initialize the model and exploration settings before training. Training results can vary because the agent uses random starting positions, action choices, and replay samples.
