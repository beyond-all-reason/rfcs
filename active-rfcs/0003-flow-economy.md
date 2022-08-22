- Start Date: 2022-07-29
- Reference Issues: N/A
- Implementation PR: TBA

# Summary

Add the capability to the engine to provide an alternative flow-economy system.

# Motivation

The current economy system in the engine lacks the ability to prorate resources to unit tasks,
leaving the burden squarely on the shoulders of the game devs. Unfortunately the game devs only
have access to imperfect knowledge about the current state of the economic changes and so are
only able to partially resolve the issue.

By handling resource proration in the engine, we avoid situations were some unit tasks are
starved and unable to proceed while other tasks are able to proceed. So if demand is twice the
supply, then all tasks will be able to progress at 50% of their intended rate.

Would be able to drop the need for economy prioritization widgets.

# Detailed design

ECS Systems introduced:
- Flow Economy
- Passive Economy Tasks
- Build
- Repair
- Reclaim
- Resurrect
- Capture
- Terraform
- Unit Resource Tracker

## Flow Economy System

This system is responsible for the allocation of resources according to the resource requests submitted. This system ticks at the rate of 10hz, or every 3 simulation frames.

> Resource Requests:
> 
> A resource request is a component that can attached to any entity that can be used to modify the resource storage. The Flow Economy system processes resource requests.
>
> A resource request can either add or use resources. An entity can have both types of requests:
> 
> - When an entity has only a Resource Use request, the Flow Economy System will try to remove the requested resources from the storage and assign a Resource Allocated component to the entity. If the resources had to be prorated then the Resource Allocated component will have a proration rate of less than 1.
> 
> - When an entity has only a Resource Add request, the Flow Economy System will add the resources to the storage.
> 
> - When an entity has both types of requests, the Flow Economy will process both as described above with one exception: if the Resource Use had to be prorated, then the resources gained from Resource Add request is reduced by the proration rate.

Entities are not permitted to take simulation affecting actions if they are tied to resource usage, unless they have been assigned a Resource Allocation component. This component details whta resources have been assigned and the proration rate applied. This allows entities to modify the rate of progress for their given task based on the proration rate.

> How to Carry out Resource-based Simulation Tasks:
> 
> - Raise the approriate Resource Request on the entity carrying out the task.
> - On the next Flow Economy tick, the system will process the request and attach a Resource Allocation component to the entity.
> - The entity can now carry out its task, adjusting progress according to whether the resources were prorated below 1.
> - Reduce the resources recorded Resource Allocation component based on how much was needed and remove the Resource Allocation component. For example, the last frame of building a unit often requires fewer resources.

When a ResourceAllocation component is destroyed, the Flow Economy System's registered observer will review whether any resources had not been used and returned those resources back to the approriate team's storage.

All Systems that make use of Flow Economy need to be aware that the Flow Economy system expects them to process all Resource Allocations BEFORE the next Flow Economy System tick. Failure to do so could result in the loss of resources.

When an entity no longer requires further resource allocations, the attached Resource Request component should be removed. This prevents the Flow Economy System processing the Resource Request in future ticks.

### Unit Passive Economy Task

A unit may have several sources of resource management, that need to be tracked separately. For example, a Command unit generates resources (Resource Add) and can carry out build orders (Resource Use.)

To support this situation, there is an Economy Task Utility that allows an arbitrary number of independant Resource Requests to be associated with a single unit. Each Economy Task is itself an entity and holds Resource Requests.

The Utilty allows for Economy Tasks to be added or removed by using a doubly-linked list component. This approach allows Systems to search through all the Economy Tasks attached to a unit.

# Drawbacks

Considerations of potential issues are listed thus:

- we still need to keep the existing system for compatibility, so this new system will need to
integrate carefully with existing code
- the addition of maybe a thousand or more lines of code
- some of the code will be of moderate complexity
- solution is part of ECS experiment so if the ECS is rejected then this will be too.

There are tradeoffs to choosing any path. Attempt to identify them here.

# Alternatives

Apart from leaving the situation as it is, only subtle variations in the technical implementation
have been considered. Alternative complete approaches have not been considered.

# Unresolved questions

- Design of the Lua API may need further thought.
- Possible opportunity to implement an alternative terrain restore command because it is in the
scope of the code effects.
