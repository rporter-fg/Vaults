[[hot]] [[testing]] [[ci/cd]] [[perception]] [[motion-planning]] [[simulation]]
https://docs.google.com/document/d/1FHnkJ9CiuahEHfO9x0mL-0JXQazFB87pxfEmV0cHzec/edit?tab=t.0

https://docs.google.com/document/d/1mxvv-NM44wfnOWHEGtlbLUaM1hzkJozJ-72zOZF-xWo/edit?tab=t.0#heading=h.qguuybfa59qo

Big ideas: we need to be able to run a virtual robot against virtual data, and use that to verify performance against code changes.

* Bag Data
	* Good for lower level testing
	* Not a true E2E test
* Simulated Image/Position Data
	* Mock out the cameras and other position sensors
	* Feed that into a virtual robot
	* Good E2E test

Remy's Testing Hierarchy:
* Unit Tests
	* Individual functions
	* Individual classes
	* Stock/known-good (or bad) data
	* Fast to execute, fast to verify
	* White-box testing
* Module Tests
	* Individual deployable units, like ROS Nodes
	* Grey-box testing
		* We only worry about the module boundaries
* System Tests
	* The whole shebang, or a meaningful subset of the whole shebang
	* Anything which interacts with the physical world needs to be mocked/twinned
	* Black-box
* Simulation Tests
	* Completely fake environment feeding data to sensors
	* Big topic, definitely not the first step- we have to get systemtests

Approaches:
* Data packs built from real-world data
	* Easiest to get started- we have it
	* Most direct comparison
	* Noisy, difficult to quantify true expectations
* Simulated data
	* Harder to make, we need a system for generating it
	* Reality of data will be harder to get correct
	* Each simulated test run can have concrete expectations
	* Feeds into a monte carlo setup

The biggest thing I see here is picking out one specific feature of the robot, like vision, and building a pipeline to test that specific module, even if it's not the whole robot at a go.

Starting point is run-per-scene, with either a real-world or generated scene.

Suggested in the doc: use [[Issac Sim]] https://developer.nvidia.com/isaac/sim, which does require [[ROS2]].