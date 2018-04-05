What Is CRAM
============

CRAM is a network flow model used to simulate water resources systems. It provides system optimization and simulation in the easy-to-use, familiar environment of Excel.

CRAM uses priority-based assignments applied to the physical constraints of a system to properly allocate water according to past, present or future operations. CRAM's interface allows users to build networks that represent real systems. The network is then forced by hydrologic time series (flow) at a consistent time step.

CRAM networks are constructed from several types of active elements, connected by nodes.  There are 8 types of active elements: Nodes, Links, Inflows, Demands, Decrees, Reservoirs, Instream Flows, and Return Flows.

Water enters the network through inflows. Like a real system, all the water that enters the system plus any change in storage at reservoirs in the system must be equal to outflows (such as through demands or links that represent river reaches that leave the study area) and losses (such as evaporation or losses to groundwater.) CRAM automatically enforces mass balance.

When CRAM solves the network, it supplies water first to those elements with the highest numerical priority, subject to any constraints, such as physical availability and capacity constraints. This makes CRAM highly suitable for analyzing systems where water rights must be administered in priority, or operations involve prioritized targets.  

Applications
^^^^^^^^^^^^

CRAM is used by many cities, states and agencies throughout the United States for their water resources modeling and decision-making. Some typical applications include:

- Simulate municipal water supply
- Evaluate changes in water demand
- Evaluate the effects of capital improvement projects
- Water allocation by water rights (prior appropriation)
- Evaluate climate change scenarios
- Manage water use within a watershed
- Evaluate water rights
- Simulate water resources facilities and their operations

Features
^^^^^^^^

- Interactive user interface
- Reservoir operations
- Trans-basin diversions
- Minimum flow requirements
- Return flows
- Groundwater
- Advanced “What-If” scenario analysis capabilities

Under the Hood
^^^^^^^^^^^^^^

CRAM optimizes systems while preserving mass balance using what is known as a circulating network. It solves the minimum-cost flow problem using the Out-of-Kilter algorithm, where flows (or some quantity) are solved for while minimizing costs.

CRAM runs within Excel, utilizing its graphics, spreadsheets and VBA code to create a familiar user interface.


