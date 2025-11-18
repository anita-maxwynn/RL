# RL: Reinforcement Learning Economic Dispatch & Power Systems

This repository provides practical code and examples for applying reinforcement learning (RL) and optimization techniques to economic dispatch in power systems. It demonstrates how to process real-world household electricity consumption data, perform optimal power flow analyses, and create RL environments for economic dispatch using modern Python tools.

**Key technologies:**  
- [PyPSA](https://pypsa.org/): Power system analysis in Python  
- [Stable-Baselines3](https://stable-baselines3.readthedocs.io/): RL library  
- Pandas, Matplotlib, Gymnasium

## Contents

- [Data Preparation](#data-preparation)
- [Power System Modeling](#power-system-modeling)
- [Reinforcement Learning Environment](#reinforcement-learning-environment)
- [Agent Training](#agent-training)
- [Usage](#usage)
- [Installation](#installation)
- [License](#license)

---

## Data Preparation

- Loads the UCI "Individual Household Electric Power Consumption" dataset with [`ucimlrepo`](https://pypi.org/project/ucimlrepo/).
- Cleans, parses timestamps, and resamples active power values to hourly data using `pandas`.
- Visualizes household electricity demand time series.

## Power System Modeling

- Uses [PyPSA](https://pypsa.org/) to construct a simple grid model:
    - One bus.
    - Two generator types (coal, gas) with different capacities and costs.
    - Household hourly load modeled as a time-varying power demand.
- Demonstrates running linear optimal power flow (LOPF) to find economic dispatch solutions.
- Plots generator outputs and compares them to system load.

## Reinforcement Learning Environment

- Implements an OpenAI Gym-compatible (now recommend [Gymnasium](https://gymnasium.farama.org/)) custom environment, `EconomicDispatchEnv`:
    - State: current power demand.
    - Action: how to split supply between generators.
    - Reward: negative total cost with heavy penalties for unmet load.
    - Handles generator constraints and dispatch logic.
- Ready to be used with standard RL libraries.

## Agent Training

- Example RL agent: trains [PPO](https://stable-baselines3.readthedocs.io/en/master/modules/ppo.html) (Proximal Policy Optimization) via [Stable-Baselines3](https://stable-baselines3.readthedocs.io/).
- Demonstrates agent–environment loop and logs training progress.

## Usage

1. **Clone the repo:**
   ```bash
   git clone https://github.com/anita-maxwynn/RL.git
   cd RL
   ```

2. **Install dependencies (in a new environment is recommended):**
   ```bash
   pip install ucimlrepo pypsa stable-baselines3 gymnasium matplotlib pandas
   ```

   *If using Colab, dependencies are installed inline in code cells.*

3. **Open notebook:**
   - Main example: [960_961_940_954.ipynb](https://github.com/anita-maxwynn/RL/blob/main/960_961_940_954.ipynb)
   - Badge for Colab: ![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)

   Or run the code directly in your Python interpreter after adapting for command-line execution.

## Project Structure

```
RL/
├── 960_961_940_954.ipynb    # Main notebook with data prep, PyPSA, RL code
├── requirements.txt         # (Optional) Python dependencies
└── (your additional files)
```

## License

Distributed under the MIT License.  
See [`LICENSE`](LICENSE) for details.

---

## References

- UCI Machine Learning Repository: [Dataset](https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption)
- [PyPSA documentation](https://pypsa.org/doc/)
- [Stable-Baselines3 documentation](https://stable-baselines3.readthedocs.io/)
- [Gymnasium migration guide](https://gymnasium.farama.org/introduction/migration_guide/)

---

## Author

Made by [anita-maxwynn](https://github.com/anita-maxwynn).

---

#### For questions, open an [issue](https://github.com/anita-maxwynn/RL/issues) or discussion.
