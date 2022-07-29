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

This will be filled out soon.

This is the bulk of the RFC. Explain the design in enough detail for somebody
familiar with BAR to understand, and for somebody familiar with the
implementation to implement. This should get into specifics and corner-cases,
and include examples of how the feature is used. Any new terminology should be
defined here.

# Drawbacks

Considerations of potential issues are listed thus:

- we still need to keep the existing system for compatibility, so this new system will need to
integrate carefully with existing code
- the addition of maybe a thousand or more lines of code
- some of the code will be of moderate complexity

There are tradeoffs to choosing any path. Attempt to identify them here.

# Alternatives

Apart from leaving the situation as it is, only subtle variations in the technical implementation
have been considered. Alternative complete approaches have not been considered.

# Unresolved questions

- Design of the Lua API may need further thought.
- Possible opportunity to implement an alternative terrain restore command because it is in the
scope of the code effects.
