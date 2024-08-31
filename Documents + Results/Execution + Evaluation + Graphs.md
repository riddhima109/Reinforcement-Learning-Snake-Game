# Execution and Evaluation

### Execution:

* The training loop in agent.py repeatedly runs games, updates the agent’s learning, and plots the results. This loop involves:
* Fetching the game state.
* Choosing an action based on the current state.
* Executing the action and observing the results.
* Training the model based on observed results.
* Plotting training progress.

By linking these components, the project creates a system where an AI agent learns to play the Snake game through reinforcement learning, continually improving its performance based on feedback from the environment.

The interface looks like-

![image](https://github.com/user-attachments/assets/ebdc0135-e0e2-413c-8010-821ea9f6bf43)

Where, the red block is the food and the blue is the snake.

On training , it generates a graph,

![image](https://github.com/user-attachments/assets/bd97030e-3064-4ec3-96f7-f3d0563e999b)

The graph in the image shows the performance of the AI agent trained using a Deep Q-Network (DQN) reinforcement model to play the Snake game. Here’s what it indicates:

* X-Axis (Number of Games): This axis represents the number of games played, ranging from 0 to approximately 120 games.
* Y-Axis (Score): This axis represents the score achieved in each game, ranging from 0 to 50.
**Key Observations:**
* Initial Performance: For the majority of the training period, the scores are very low, close to zero. This indicates that the AI agent initially struggles to perform well in the game.
* Learning Phase: Towards the end of the training, there is a significant spike in the scores, with one peak reaching up to 39. This suggests that the AI agent has learned an effective strategy to play the game better after many iterations.
* Improvement Over Time: The sudden increase in scores towards the end shows that the AI agent improves its performance significantly as it continues to learn from its experiences.

This graph demonstrates the typical learning curve of a reinforcement learning model, where the agent initially performs poorly but gradually improves as it learns from its interactions with the environment. The spike in scores indicates a breakthrough in the agent’s learning process, where it starts to achieve higher scores consistently.

On evaluating the performance of agent for 10 episodes , it outputs-

![image](https://github.com/user-attachments/assets/0c86699e-8974-45a6-930b-2e8346043fd6)

Running an evaluation code for the DQN reinforcement model in the Snake game typically involves assessing the performance of the trained AI agent over a series of episodes. The output you provided shows the results of ten episodes, with metrics such as “Score,” “Average Score,” and “Highest Score” for each episode.

**Key Metrics Explained:**

* **Episode:** This indicates the specific trial or run of the game. For example, “Episode: 1/10” means the first out of ten episodes.
* **Score:** The score achieved by the AI agent in that particular episode. For instance, in Episode 3, the score is 186.
* **Average Score:** The average score across all episodes up to that point. For example, after Episode 3, the average score is 82.33.
* **Highest Score:** The highest score achieved in any of the episodes so far. For example, the highest score is 186 after Episode 3.

### Purpose of Evaluation:
* **Performance Tracking:** By running multiple episodes, you can track how well the AI agent performs on average and identify any improvements or regressions.
* **Consistency Check:** Evaluating over several episodes helps in understanding the consistency of the agent’s performance.
* **Model Validation:** It helps in validating whether the trained model is effective and generalizes well to different game scenarios.

This evaluation process is crucial for understanding the effectiveness of the training and making any necessary adjustments to improve the AI agent’s performance.
