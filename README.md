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

My contribution was turning that training skeleton into a working learning loop. I reset the maze at a random free cell, selected actions through exploration or the highest predicted Q-value, and recorded each action's state, reward, next state, and completion flag. I connected replay batches to the training helper, updated the target network periodically, and tracked wins and losses. The final notebook uses a 32-game history window and requires both a full window of wins and a successful completion check before stopping early. Comparing the unfinished Week 5 milestone with the Week 7 notebook shows how I connected the supplied components into the agent's training process.

### What do computer scientists do, and why does it matter?

Computer scientists translate problems into representations that computers can work with, design algorithms, and evaluate whether the results meet people's needs. In this project, that meant representing the maze as numerical state information and learning which actions could lead to the treasure. This work matters because the same problem-solving skills support systems that help people make decisions, recognize patterns, and automate tasks. Choosing a suitable method and explaining its limitations are part of that responsibility. A learned maze policy demonstrates reinforcement learning, while a known map could also be approached with a graph search algorithm.

### How do I approach a problem as a computer scientist?

I begin by defining the goal, identifying constraints, and deciding what evidence would demonstrate success. I then break the problem into smaller parts, understand the existing code, and establish a baseline before changing parameters. My Week 2 MNIST experiments showed why this matters: increasing training from 100 to 200 epochs improved training accuracy much more than validation accuracy. That helped me recognize diminishing returns and the need to evaluate performance beyond the training data.

The course gradually connected these ideas. Week 3 extended neural networks to CIFAR-10 image classification with convolutional layers. The CartPole work in Weeks 5 and 6 introduced and revisited learning from actions and rewards, including exploration, experience replay, and target networks. I applied those concepts to the pirate agent in Week 7. For this project, evaluating different starting cells is more meaningful than watching one successful game. Success on the supplied maze still does not establish a shortest route or show that the agent will succeed on an unfamiliar maze.

### What are my ethical responsibilities to the end user and the organization?

I am responsible for considering how a system's decisions affect the people who use it and the people represented in its data. My Week 1 AI assistant proposal emphasized preserving user control over important decisions. The Week 3 image classification analysis and Week 4 recommendation-system project developed that thinking through questions about bias, privacy, and data collection. These assignments taught me to consider whose needs the system serves, whether the data represents its users, and whether an optimization goal could encourage harmful behavior.

For end users, I should protect personal information, explain limitations clearly, and provide meaningful control where automated decisions affect them. For an organization, I should produce maintainable code, document assumptions, evaluate reliability and unequal outcomes, and communicate risks honestly. In the pirate project, that includes distinguishing a recent win rate from broader evidence of reliable behavior and acknowledging that the reward design influences what the agent learns. A system's success metric needs to reflect the intended outcome for its users.

## Running the notebook

From the repository directory, install the dependencies and launch JupyterLab:

```bash
python -m pip install -r requirements.txt jupyterlab
python -m jupyterlab Michael_Foster_ProjectTwo.ipynb
```

Keep both Python helper files in the same directory as the notebook. Run the cells in order from a fresh kernel to initialize the model and exploration settings before training. Training results can vary because the agent uses random starting positions, action choices, and replay samples.
