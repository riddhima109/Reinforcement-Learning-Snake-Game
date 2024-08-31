# Reinforcement-Learning-Snake-Game

This project showcases the implementation of a classic Snake Game using Reinforcement Learning (RL). The aim is to train an intelligent agent that learns to play Snake autonomously using RL techniques, specifically Deep Q-Learning (DQN). The project highlights how RL can be applied to game environments, transforming them into learning platforms where agents develop strategies through interaction and feedback.

The project demonstrates how RL can be used to make the agent learn optimal policies, such as how to navigate the grid, avoid collisions, and maximize the score by eating as many food items as possible.

## **Project Structure**

The repository is organized as follows:

  - **`snake_game.py`**: Implements the Snake game logic that is playd by human.
  - **`snake_gameai.py`**: Implements the Snake game logic that is playd by AI agent.
  - **`agent.py`**: Contains the RL agent code, including the DQN algorithm.
  - **`arial.ttf`**: Contains the font
  - **`helper.py`**: Contains a function to plot and update the training scores and their moving average in real-time, useful for visualizing the progress of a reinforcement learning model.
  - **`model.py`**: Defines the neural network architecture for the Q-function.
  - **`README.md`**: Project documentation.
  - **`requirements.txt`**: List of dependencies required to run the project.

## **Reinforcement Learning Overview**

Reinforcement Learning (RL) is a feedback-based machine learning paradigm where an agent learns to make decisions by interacting with an environment. The agent receives feedback from its actions in the form of rewards, which guide its learning process. The goal is to learn a policy that maximizes cumulative rewards over time.

### **Q-Learning**

Q-Learning is a value-based RL algorithm where the agent learns a Q-function, which estimates the expected cumulative reward for taking a given action in a given state. The Q-function is updated iteratively using the Bellman equation:

![image](https://github.com/user-attachments/assets/3223e05f-e0ce-4cd9-b21d-77aba0f020f9)

Where:
- ( s ) is the current state.
- ( a ) is the current action.
- ( r ) is the reward received after taking action \( a \).
- ( s') is the next state.
- ( alpha ) is the learning rate.
- ( gamma ) is the discount factor.

### **Deep Q-Learning (DQN)**

Deep Q-Learning (DQN) is an extension of Q-Learning where the Q-function is approximated using a deep neural network. This allows the agent to handle high-dimensional state spaces, making it suitable for environments like the Snake Game.

The DQN algorithm introduces two key innovations:
1. **Experience Replay**: Stores agent experiences in a replay buffer and samples mini-batches during training. This reduces correlations between consecutive experiences and stabilizes learning.
2. **Target Network**: A separate network used to compute target Q-values, updated periodically to prevent instability in training.

## **Game Logic**

### **Environment Setup**

The Snake Game environment is a grid where the snake moves to eat food and grows in length. The game ends if the snake collides with itself or the walls. The environment is fully observable, with the entire grid and snake's state accessible to the agent.

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
- **+10**: For eating food.
- **-10**: For colliding with a wall or the snake's body.
- **0**: For all other actions.

The sparse nature of the rewards encourages the agent to learn long-term strategies for survival and maximizing the score.

## **Training Process**

### **Hyperparameters**

Key hyperparameters for the DQN model include:
- **Learning Rate (( alpha ))**: Controls the step size in updating Q-values.
- **Discount Factor (( gamma ))**: Determines the importance of future rewards.
- **Epsilon (( epsilon ))**: Governs the exploration-exploitation trade-off.
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

## Installation

### **Prerequisites**

Ensure you have the following dependencies installed:
- Python 3.x
- TensorFlow or PyTorch (depending on the framework used for the DQN)
- NumPy
- Matplotlib
- Gym (for environment simulation)

### Installation

Clone the repository and install the required dependencies:

```bash
git clone https://github.com/riddhima109/Reinforcement-Learning-Snake-Game.git
cd Reinforcement-Learning-Snake-Game
pip install -r requirements.txt
```

# Project Overview 

* **What is the pupose of this project?**
  
The purpose of this project is to implement a classic Snake game using Pygame, serving as a practical exercise in game development and programming. It provides:

1. **Learning Experience**: Offers hands-on experience with Pygame for graphics rendering, user input handling, and game logic.
2. **Foundation for AI Development**: Serves as a baseline environment where reinforcement learning algorithms can be tested and developed, given that the Snake game’s mechanics are straightforward and well-defined.
3. **Interactive Coding Practice**: Helps improve coding skills by implementing and debugging a real-time interactive application with dynamic updates and user interactions.

Overall, it’s a foundational project that helps in understanding game development principles and can be expanded for more complex applications or integrated with AI techniques.

* **What is the motivation behind this project?**
  
The motivation behind this project is multi-faceted:

1. **Educational Purpose**: To provide a hands-on learning experience in game development using Pygame, helping individuals understand core programming concepts and the implementation of graphical interfaces.

2. **Reinforcement Learning Testing**: To create a controlled environment for testing and experimenting with reinforcement learning algorithms. The Snake game’s clear rules and objectives make it an ideal candidate for such experiments.

3. **Skill Development**: To enhance programming skills, particularly in Python, by developing a complete game from scratch. This includes handling real-time user input, managing game state, and rendering graphics.

4. **Foundation for Further Projects**: To serve as a foundational project that can be built upon for more advanced projects, such as integrating AI, developing more complex game mechanics, or creating other types of interactive applications.

Overall, the project aims to blend practical coding experience with opportunities for applying and testing advanced concepts in a fun and engaging way.

* **Why Pygame is Used?**
  
Pygame is used in this project to create and manage the graphical interface for the Snake game. It provides tools for:

1. **Graphics and Rendering**: Drawing the game elements like the snake, food, and score on the screen.
2. **Event Handling**: Capturing user input from keyboard events to control the snake's direction.
3. **Game Loop Management**: Updating the game state and refreshing the display at a consistent frame rate.
4. **Sound**: Adding sound effects (though not used in this specific code) to enhance the gaming experience.

Overall, Pygame simplifies game development by providing an easy-to-use interface for handling these common game development tasks.

* **What can be the future developments?**
  
Future developments for the Snake game project could include:

1. **AI Integration**: Implementing AI techniques, such as reinforcement learning algorithms, to enable the snake to play autonomously and improve its performance over time.

2. **Enhanced Graphics and UI**: Upgrading the visual elements, adding animations, and improving the user interface for a more polished and engaging experience.

3. **Additional Features**: Introducing new game mechanics such as obstacles, power-ups, or different game modes to increase complexity and variety.

4. **Multiplayer Mode**: Developing a multiplayer mode where multiple players can compete or cooperate in real-time, adding a social element to the game.

5. **Level Progression**: Adding a system of levels or increasing difficulty as the player progresses, to keep the game challenging and engaging.

6. **Leaderboard and Scoring**: Implementing a leaderboard system to track and compare high scores, adding a competitive aspect to the game.

7. **Cross-Platform Support**: Adapting the game for different platforms, including mobile devices or web browsers, to reach a broader audience.

8. **Sound and Music**: Incorporating sound effects and background music to enhance the gaming experience and create a more immersive environment.

These developments can enhance the game's functionality, increase its appeal, and provide opportunities for further learning and experimentation.

