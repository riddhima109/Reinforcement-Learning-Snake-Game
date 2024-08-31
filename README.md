# Reinforcement-Learning-Snake-Game



This project showcases the implementation of a classic Snake Game using Reinforcement Learning (RL). The aim is to train an intelligent agent that learns to play Snake autonomously using RL techniques, specifically Deep Q-Learning (DQN). The project highlights how RL can be applied to game environments, transforming them into learning platforms where agents develop strategies through interaction and feedback.

The project demonstrates how RL can be used to make the agent learn optimal policies, such as how to navigate the grid, avoid collisions, and maximize the score by eating as many apples as possible.

## **Project Structure**

The repository is organized as follows:

- **`/src`**: Contains the source code for the game and RL algorithms.
  - **`game.py`**: Implements the Snake game logic.
  - **`agent.py`**: Contains the RL agent code, including the DQN algorithm.
  - **`model.py`**: Defines the neural network architecture for the Q-function.
  - **`train.py`**: Handles the training loop, including experience replay and epsilon decay.
  - **`utils.py`**: Utility functions for the project.
- **`/data`**: Directory for storing training data, models, and logs.
- **`/notebooks`**: Jupyter notebooks for exploratory data analysis (EDA) and experimentation.
- **`README.md`**: Project documentation.
- **`requirements.txt`**: List of dependencies required to run the project.
- **`LICENSE`**: Licensing information.

## **Reinforcement Learning Overview**

Reinforcement Learning (RL) is a machine learning paradigm where an agent learns to make decisions by interacting with an environment. The agent receives feedback from its actions in the form of rewards, which guide its learning process. The goal is to learn a policy that maximizes cumulative rewards over time.

### **Q-Learning**

Q-Learning is a value-based RL algorithm where the agent learns a Q-function, which estimates the expected cumulative reward for taking a given action in a given state. The Q-function is updated iteratively using the Bellman equation:

\[
Q(s, a) \leftarrow Q(s, a) + \alpha \left( r + \gamma \max_a Q(s', a') - Q(s, a) \right)
\]

Where:
- \( s \) is the current state.
- \( a \) is the current action.
- \( r \) is the reward received after taking action \( a \).
- \( s' \) is the next state.
- \( \alpha \) is the learning rate.
- \( \gamma \) is the discount factor.

### **Deep Q-Learning (DQN)**

Deep Q-Learning (DQN) is an extension of Q-Learning where the Q-function is approximated using a deep neural network. This allows the agent to handle high-dimensional state spaces, making it suitable for environments like the Snake Game.

The DQN algorithm introduces two key innovations:
1. **Experience Replay**: Stores agent experiences in a replay buffer and samples mini-batches during training. This reduces correlations between consecutive experiences and stabilizes learning.
2. **Target Network**: A separate network used to compute target Q-values, updated periodically to prevent instability in training.

## **Game Logic**

### **Environment Setup**

The Snake Game environment is a grid where the snake moves to eat apples and grows in length. The game ends if the snake collides with itself or the walls. The environment is fully observable, with the entire grid and snake's state accessible to the agent.

### **State Representation**

The state is represented as a matrix encoding the position of the snake's head, its body, and the apple. This can be flattened into a vector for input into the neural network. The state also includes directional information to help the agent understand the snake's current movement direction.

### **Action Space**

The action space consists of four possible actions:
- Move Up
- Move Down
- Move Left
- Move Right

The agent selects an action based on the current state to maximize the expected future reward.

### **Reward Function**

The reward function is critical to guiding the agent's learning. The rewards are defined as:
- **+10**: For eating an apple.
- **-1**: For colliding with a wall or the snake's body.
- **0**: For all other actions.

The sparse nature of the rewards encourages the agent to learn long-term strategies for survival and maximizing the score.

## **Training Process**

### **Hyperparameters**

Key hyperparameters for the DQN model include:
- **Learning Rate (\( \alpha \))**: Controls the step size in updating Q-values.
- **Discount Factor (\( \gamma \))**: Determines the importance of future rewards.
- **Epsilon (\( \epsilon \))**: Governs the exploration-exploitation trade-off.
- **Batch Size**: Number of experiences sampled from the replay buffer per update.
- **Replay Buffer Size**: The capacity of the experience replay buffer.
- **Target Network Update Frequency**: How often the target network is updated.

### **Training Loop**

1. **Initialization**: The environment and agent are initialized. The agent starts with an empty replay buffer and an initial epsilon value for exploration.
2. **Episode Loop**: The agent interacts with the environment over multiple episodes. In each episode:
   - The agent observes the current state.
   - An action is selected using an epsilon-greedy policy.
   - The environment transitions to the next state, and the agent receives a reward.
   - The experience (state, action, reward, next state) is stored in the replay buffer.
   - A mini-batch of experiences is sampled from the buffer to update the Q-network.
3. **Target Network Update**: Periodically, the weights of the target network are updated to match the Q-network.
4. **Epsilon Decay**: Epsilon is gradually reduced to shift from exploration to exploitation as training progresses.

### **Exploration vs. Exploitation**

The epsilon-greedy policy balances exploration (trying new actions) and exploitation (using known actions that yield high rewards). Initially, exploration is emphasized to discover a wide range of states and actions. As training progresses, the agent increasingly exploits the learned policy to maximize rewards.

### **Model Evaluation**

After training, the agent's performance is evaluated by playing the game using the learned policy. Metrics such as average score, survival time, and the number of apples eaten are tracked to assess the model's effectiveness.

## **Results and Performance**

### **Training Metrics**

Training metrics include the average reward per episode, Q-value estimates, and loss values. These metrics are plotted to visualize the agent's learning curve and monitor progress.

### **Gameplay Visualization**

The agent's gameplay can be visualized to observe the learned strategy. This includes how the agent navigates the grid, avoids collisions, and targets apples. Visualization helps in understanding the agent's behavior and identifying areas for improvement.

## **Installation and Usage**

### **Prerequisites**

Ensure you have the following dependencies installed:
- Python 3.x
- TensorFlow or PyTorch (depending on the framework used for the DQN)
- NumPy
- Matplotlib
- Gym (for environment simulation)

### **Installation**

Clone the repository and install the required dependencies:

```bash
git clone https://github.com/riddhima109/Reinforcement-Learning-Snake-Game.git
cd Reinforcement-Learning-Snake-Game
pip install -r requirements.txt
```

### **Running the Game**

You can run the Snake game manually to familiarize yourself with the environment:

```bash
python src/game.py
```

### **Training the Model**

To train the RL agent, run the training script:

```bash
python src/train.py
```

Training logs and model checkpoints will be saved in the `/data` directory.

### **Evaluating the Model**

After training, evaluate the agent's performance by running:

```bash
python src/evaluate.py
```

This will load the trained model and run episodes to assess its

