# Parent-child pipeline

https://docs.gitlab.com/ee/ci/pipelines/pipeline_architectures.html#basic-pipelines

## Case

If we need to build two packages independently, you can use parent-child pipelines.
See the diagram below.

![DAG_pipelines](./img/DAG_pipelines.png)

We can create one parent .gitlab-ci.yml and some children.
For relationship we need to use:

- The **rules** keyword: For example, have the child pipelines triggered only when there are changes to that area.

and

- The **include** keyword: Bring in common behaviors, ensuring you are not repeating yourself.

## Solution

See parent pipeline in the [.gitlab-ci.yml](./.gitlab-ci.yml)

and two children's pipelines in the

[/a/.gitlab-ci.yml](./a/.gitlab-ci.yml)

and

[/b/.gitlab-ci.yml](./b/.gitlab-ci.yml)
