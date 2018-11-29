# git-maven-versioning-plugin + enforcer-plugin

The repository contains an example of a Maven multimodule project with two plugins.
Enforcer plugin searches dependencies with different versions and fails a build in this case.

In every module, we use ${project.version} to specify dependencies on another module.

So, when we try to build the project, we get an error message: 
```
[WARNING] Missing POM for mgve-example:printer:jar:1.0.0-TICKET-123-description-TICKET-123-description-SNAPSHOT
[WARNING]
Dependency convergence error for mgve-example:printer:1.0.0-TICKET-123-description-TICKET-123-description-SNAPSHOT paths to dependency are:
+-mgve-example:world-greater:1.0.0-TICKET-123-description-SNAPSHOT
  +-mgve-example:greater:1.0.0-TICKET-123-description-SNAPSHOT
    +-mgve-example:printer:1.0.0-TICKET-123-description-TICKET-123-description-SNAPSHOT
and
+-mgve-example:world-greater:1.0.0-TICKET-123-description-SNAPSHOT
  +-mgve-example:printer:1.0.0-TICKET-123-description-SNAPSHOT

[WARNING] Rule 0: org.apache.maven.plugins.enforcer.DependencyConvergence failed with message:
Failed while enforcing releasability the error(s) are [
Dependency convergence error for mgve-example:printer:1.0.0-TICKET-123-description-TICKET-123-description-SNAPSHOT paths to dependency are:
+-mgve-example:world-greater:1.0.0-TICKET-123-description-SNAPSHOT
  +-mgve-example:greater:1.0.0-TICKET-123-description-SNAPSHOT
    +-mgve-example:printer:1.0.0-TICKET-123-description-TICKET-123-description-SNAPSHOT
and
+-mgve-example:world-greater:1.0.0-TICKET-123-description-SNAPSHOT
  +-mgve-example:printer:1.0.0-TICKET-123-description-SNAPSHOT
]
```

It can be workarounded if we will use ${parent.version} or set version with dependencyManagement.
But I want to find a correct way to use the common version across the multimodule project.