# Meshtastic Discrete-Event Simulator – Assignment EX2

## 📝 Assignment Description

In this assignment, we were asked to:
- Understand the basic principles of the **Meshtastic** communication system.
- **Design and implement** a **time-discrete simulator** for a Meshtastic network.
- Support **at least 100 nodes** (clients) in simulation.
- Include a **flexible configurator** to modify key parameters.
- Provide **statistics** about messages sent/received.
- Optionally include a **GUI for debugging**.
- Include some form of **RF link budget model**.
- It is permitted (and recommended) to use **open-source projects**.

---

## ✅ Solution Overview

To meet the assignment requirements, I used the official open-source project:  
👉 [`Meshtasticator`](https://github.com/meshtastic/Meshtasticator)

This is a Python-based discrete-event simulator developed by the Meshtastic team. It simulates the radio behavior of Meshtastic devices, allowing message scheduling, routing, propagation modeling, and logging of statistics.

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/meshtastic/Meshtasticator.git
cd Meshtasticator
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run simulation with 100 nodes (non-GUI mode)
```bash
python3 loraMesh.py 100
```

### 4. (Optional) Run with GUI for manual node placement
```bash
python3 loraMesh.py
```

---

## ⚙️ Configuration Options

You can edit `lib/config.py` to change:

- `MODEM`: Set radio mode (e.g., SF7-SF12)
- `PERIOD`: Mean time between messages per node
- `PKT_LEN`: Packet size in bytes
- `PROP_MODEL`: RF propagation model (e.g., log-distance, Okumura-Hata)
- `DMs`: Use direct messaging instead of broadcast
- `MINDIST`: Minimum spacing between nodes

---

## 📊 Output and Statistics

The simulator generates:
- A visual plot of node layout and message timeline
- A summary of:
  - Number of messages sent per node
  - Number of messages received
  - Duplicate message ratio
  - Collisions
  - Average number of hops
- Optional batch results saved in `/out/report/` when using `batchSim.py`

---

## 🧪 Example Scenario

I ran a simulation of 100 nodes using:
- Broadcast messages
- Log-distance RF model
- SF7 radio setting
- Mean message interval of 300 seconds

The simulation showed:
- High reachability across the mesh
- Some message duplication due to rebroadcasting
- Collision events depending on node density

---

## 🖥️ GUI (Optional for Debugging)

When running `loraMesh.py` without arguments:
- A GUI window appears
- You can place nodes manually and configure each one (router, hop limit, etc.)
- Click "Start" to begin the simulation

---

## ✅ How This Meets Assignment Requirements

| Requirement                              | Fulfilled? | How                                             |
|------------------------------------------|------------|--------------------------------------------------|
| Time-discrete simulator                  | ✅          | Based on SimPy discrete-event simulation         |
| 100+ clients                             | ✅          | Supports any number of nodes (tested with 100)   |
| Flexible configurator                    | ✅          | Via `config.py` and optional GUI                 |
| Message statistics                       | ✅          | Sent/received/duplicate/collision stats tracked  |
| Representation of results                | ✅          | Graphs and plots generated at the end            |
| GUI for debugging                        | ✅ (optional) | Included but not mandatory                       |
| RF link budget model                     | ✅          | Multiple path-loss models supported              |

---

## 📁 Files in This Project

- `loraMesh.py`: Main simulator
- `lib/config.py`: Configuration settings
- `batchSim.py`: Run multiple simulations for statistical analysis
- `plotExample.py`: Plot results from batch runs
- `/out/`: Output folder for logs, node configs, and reports

---

## 🙋‍♂️ Notes

- If the GUI crashes on your system, simply run `loraMesh.py` with a node count argument to bypass the interactive window.
- The simulation can be extended with different propagation models or custom routing logic if needed.

---

## 📅 Author & Course Info

**Student Name:** [Your Name]  
**Course:** Economic Algorithms / Networking Systems  
**Assignment:** EX2 - Meshtastic Time-Discrete Simulator  
**Year:** 2025
