#### Salt Stack
- One system runs the *salt master*, and all other systems run the *salt-minion*
	- Master pushes a job to be executed, minions subscribe to those jobs
	- Indicate which minions should execute through *targets*, which can include minion *grains*
- Jobs can be run ad-hoc 
- States are YAML files that specify what state a target system should be in (managed file, installed package, or config)
- Pillars can be used to distribute secrets to specific systems
- Beacons and Reactors can listen and respond to system events