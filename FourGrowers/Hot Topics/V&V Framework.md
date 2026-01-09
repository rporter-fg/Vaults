[[hot]]
This seems to build off of the [[Virtual Simulation Pipeline]]. It seems like once we *have* that, running it as part of CI/CD becomes easy.

Core goal: take key metrics around [[recall]], [[precision]] and [[speed]], w/ [[speed]] subdivided across different portions of the work.

Overall robot performance can be viewed as a polytope. Each metric is a radial rotation around a center, with a weight attached. The `r` of the point is `value * weight` . The area of the described shape is the overall robot performance, and we can start requiring that every PR increases that envelope.

The weighting gives us the flexibility to decide tradeoffs- if [[recall]] is more important than [[speed]] we can weight it higher- meaning drops in recall will impact the performance envelope more than drops in speed.

Workflow is: run the simulation, grab the bag files, aggregate the metrics from the bag. 

## Goals
* Extract key metrics from a CI pipeline and report the results as part of the CI process
	* Maybe reuse/readapt the existing extractor Python scripts
* Set thresholds and tests around those metrics to ensure that they don't drop relative to the current release
	* The `master` branch will have a copy of the last report for its run
	* We compare the two reports
* Set up business process for understanding how we apply the report
	* How do we decide weights?
	* How do we decide what counts as a stopping violation vs. a "it's a reasonable tradeoff"?