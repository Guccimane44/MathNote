# Applying ML to HPC Notes

## Some Terminologies
* A __Simulation__ refers to the process of using computational models and algorithms to replicate the behavior of a real-world system or process.
* A __Campaign__ typically refers to a set of coordinated and planned computational tasks or simulations conducted with specific objectives.
* A __Surrogate Model__, also known as a surrogate or metamodel, is a simplified and computationally efficient representation of a more complex and computationally expensive simulation or optimization model. The purpose of using a surrogate model is to approximate the behavior of the original model while significantly reducing the computational cost.
* __Differences between a model and a simulation:__ a model is a conceptual or mathematical representation of a system, while a simulation is the computational execution of that model to mimic the behavior of the real-world system.
* __Simulation approach versus MLaroundHPC approach__:Traditional Simulation approach relies on designing an excellent model, while ML approach focuses on the learning patterns acquired from data for predictions or classifications.  

## Motivation
The HPC communities have previously mistakenly assumed that as long as performance gains from hardware are possible, traditional simulation-based methods will continue to provide increased scientific insight. This insight has been challenged at the current time when we can foresee the obsolescence of Moore's law. It is urgent to examine the methodological efficiency otherwise we may be reaching limits of both hardware and methodological performance gains.
## Learning Everywhere: application fields

##### ML around HPC:
Using ML to learn from simulations and produce learned surrogates for the simulations. This increases effective performance for strong scaling.
* Learning Outputs from Inputs: Use performed simulation to directly train an AI system.
* Learning Simulation Behavior: Use ML surrogates to learn the system/model behavior. HPC system usually is computationally heavy. Once we have built the ML surrogates, we can apply them to learning the behaviors of the HPC system/model.
* Faster and Accurate PDE Solutions: Applying ML algorithms to reduce the time costs on high dimensional PDE computations on HPC.
* New approach to Multi-Scale Modelling: Multi-Scale Modelling is a modeling method that uses multiple scales instead of one. The deployment of machine learning can simplify the process of finding potential Multi-Scale.
##### ML Control
* Experiment Control: Using ML to build the simulation surrogates for simulations, when simulations are used in the control of experiments and objective-driven computational campaigns.
* Experiment Design: Model-based design of experiments with new ML assistance can identify the optimal conditions for stimuli and measurements that yield the most information about the system given practical limitations on realistic experiments. In other words, it helps the model design by giving more information about the structures and parameters of ongoing projects.
##### ML Auto-Tunning
* ML can be used for a range of tuning and optimization objectives.
##### ML After HPC
* ML analyzing results of HPC as in trajectory analysis and structure identification in biomolecular simulations.
## ML around HPC Classification and Exemplars.
The interaction between models and simulation data occurs in two directions: 
1) How to use multi-modal data (data in various forms, like text, images, or audio) to inform complex models in the presence of uncertainty. In simple terms: we have lots of data in various forms but we might not be sure how useful they can be. How can we use those data in the model? (how to use the acquired data?)
2) How, where, when, and from which source to acquire simulation data to optimally inform models with respect to a particular goal or goals is fundamentally an optimal experimental design problem. (how to acquire the proper data)

Therefore we have the urge to distinguish different modes and mechanics of how learning is integrated with HPC simulations. In other words, we need to distinguish different interactions of learning and HPC. The three primary modes and mechanisms for integrating learning with HPC simulations are:
##### Substitution
A surrogate model is used to substitute an essential element of the original simulation (method). The surrogate model is used to create multi-scale or coarse-grained surrogate modeling, which could either learn the structure or theory of the original simulation. For example: Using a trained Neural Network from the original simulation can reduce the cost significantly compared to running it in the original simulation. 
##### Assimilation
In this mode, data from simulations, offline external constraints, or real-time experiments are integrated into physics-based models, which are then assimilated into traditional simulations. For example: In weather prediction, we constantly assimilate new, time-dependent, based on observations corrected simulations into the traditional simulation model. 
##### Control and Adaptive Execution
In this mode, the simulation is controlled towards important and interesting parts of the simulation phase space. Sometimes this involves determining the parameters of the next stage (iteration) of simulations based on intermediate data. Sometimes the entire campaign can be adaptively steered towards an objective, which in turn could involve getting better data via active learning based upon an objective function. In other words, we steer the simulation towards the objectives so that we might have more fitting data for the campaign.
## ML Around HPC Cyber Infrastructure



