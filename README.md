- Creating simple Gluster cluster using Ansible


Gluster is a scalable, distributed file system that aggregates disk storage resources from multiple servers into a single global namespace.

An arbitrated replicated volume, or arbiter volume, is a three-way replicated volume where every third brick is a special type of brick called an arbiter. Arbiter bricks do not store file data; they only store file names, structure, and metadata. The arbiter uses client quorum to compare this metadata with the metadata of the other nodes to ensure consistency in the volume and prevent split-brain conditions.

Advantages of arbitrated replicated volumes

- Better consistency
    When an arbiter is configured, arbitration logic uses client-side quorum in auto mode to prevent file operations that would lead to split-brain conditions. 
- Less disk space required
    Because an arbiter brick only stores file names and metadata, an arbiter brick can be much smaller than the other bricks in the volume. 
- Fewer nodes required
    The node that contains the arbiter brick of one volume can be configured with the data brick of another volume. This "chaining" configuration allows you to use fewer nodes to fulfill your overall storage requirements. 
- Easy migration from two-way replicated volumes
    Red Hat Gluster Storage can convert a two-way replicated volume into an arbitrated replicated volume
	
	
Disadvantages:
- Although arbitrated replicated volumes provide better data consistency than a two-way replicated volume, because they store only metadata, they provide the same level of     availability as a two-way replicated volume. To achieve high-availability, you need to use a three-way replicated volume instead of an arbitrated replicated volume.
