# A Multi-Objective VRP Solver using a Hybrid Memetic Algorithm
>  by Rayan Hashemy

### Moving Beyond Just the 'Cheapest' Route

In supply chain, we're always chasing efficiency. But for a long time, that just meant one thing: finding the shortest, cheapest route possible. The problem is, the real world is a lot more complicated. The shortest route is rarely the best one.

What happens if the cheapest route has the highest C02 emissions? Or what if it makes your most VIP customer upset because they get their delivery last? This is the strategic puzzle that has fascinated me, and it's the problem I built this project to solve.

I chose these three compelling objectives for this project, as I have found these to be the most common objectives companies in the Supply chain industry are focusing on:
*   Economic Cost (total distance)
*   Environmental Impact (CO2 emissions)
*   Customer Service (prioritizing VIPs)

### 2. My Approach: How I Built a Smarter AI

My goal was to build an AI that could deliver a menu of optimal choices, which is called a Pareto Front—rather than a single, one-size-fits-all answer. I built the project in two main phases.

#### **Phase 1: The NSGA-II Baseline**
I started by implementing a Non-dominated Sorting Genetic Algorithm II (NSGA-II). This is a powerful evolutionary algorithm that's great at exploring all the possible solutions and finding a good set of compromises. This acts as the global strategist for the model.

#### **Phase 2: The Upgrade with ALNS**
After analyzing the results, I knew it its efficeny as not being optimzed smart enough. The baseline model was good at finding generally good routes, but struggled to refine them. So, I did more research and decided to build a hybrid Memetic Algorithm. I integrated an Adaptive Large Neighborhood Search (ALNS) to act as a local expert, or personal trainer for optimal routes found bt the NSGA model.

Instead of a simple, random mutation, each new route created by the GA is sent to the ALNS for an intense destroy and repair session. This allows the model to intelligently analyze and optimize each route at a local level, leading to a much more powerful and efficient search.

### 3. Key Features & How It Works

*   **Multi-Objective Optimization:** The entire system is guided by three custom functions that score every route on Cost, CO2, and a unique "VIP Lateness" metric I designed to penalize routes that serve key accounts late.
*   **Hybrid Memetic Algorithm:** This approach combines the global population management of NSGA-II with the intense, targeted local search of ALNS.
*   **Realistic Problem Environment:** The model operates on a simulated dataset of 50 customers with different priority levels, a central depot, and different vehicle types with unique CO2 emission factors.

### 4. Results & Impact

The decision to integrate ALNS was a definitive success. The new hybrid model discovered a set of solutions that were quantifiably superior to the baseline model.

Generations for NSGA model
![1753175009283](https://github.com/user-attachments/assets/084dc535-5a9f-4098-ae2e-fa8c3c746739)

Generations for hybrid NSGA and ALNS model
<img width="1490" height="490" alt="download" src="https://github.com/user-attachments/assets/2aa9cf2a-7d42-47e0-a118-8900b73aaa6f" />

Results of Hybrid Model
<img width="1989" height="1189" alt="download (1)" src="https://github.com/user-attachments/assets/08d49ed1-2553-40d7-8e75-9b4fd4fef25d" />


*   **Proven Performance:** The hybrid model found a 'Most Cost-Focused' route that was **7% more efficient** than the best route from the standard NSGA-II model.
*   **Strategic Decision Support:** The final output provides a clear, data-driven menu of elite solutions, empowering a business to choose a route that directly aligns with its strategic priority for the day.

### 5. Technologies Used
Core Development:
**Language: Python
**Libraries: Pandas for data manipulation, NumPy for numerical operations, and Matplotlib for visualization.
**Environment: Google Colab

Research & Prototyping:
**AI Research Assistants : Used to accelerate the initial literature review and synthesize key concepts from academic papers. (Elicit)
**AI Code Assistants : Leveraged for boilerplate code generation, debugging, and accelerating the overall prototyping and development process. (Claude,Gemini)
