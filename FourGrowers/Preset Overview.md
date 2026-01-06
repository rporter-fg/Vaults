[[Preset]] is a third party product that we integrate with. Based on [[Apache Superset]].
[[Snowflake]] as the backend database.

[[Preset]] is basically [[Remy's Law of Requirements Gathering]]- it's excel, wired up to our stream.

Migrate from [[Nix]] to [[Bazel]].

[[rosbag]]s go up into [[AWS]], triggers a [[Lambda]], which spins up a container that downloads the bag, extracts the log, and then pushes it up into [[Snowflake]].

Database defined in [[Alembic]], a python based DB migration tool. Schemas defined in [[SQL Alchemy]].

[[Terraform]] for infra as code, Github autopushes prod to AWS.

Problems: 
* Debuggability, failure recovery 
* Only get HMI data, and metrics
	* We want more topics, aka temperature
Goals:
* Nix - Bazel
* Expand metrics in Snowflake
* ROS2 support
* Infra changes as required
* Better dashboards and more searchable dashboards
* Explore crosslinking in Preset
* 