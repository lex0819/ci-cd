# add Personal Access Token

in gitlab click
user icon -> edit profile -> Access Tokens -> Add new token

token name = RUNNER_TOKEN - it's come up name
Expiration date = after long time

check api
Grants complete read/write access to the API, including all groups and projects, the container registry, the dependency proxy, and the package registry.

Create OK
It returns
Your new personal access token
glpat-aKr-ibCNkmjims8YQguW

# add new token to Variables

Settings -> CI/CD -> Variables expand
Add variable
Env = default

check mask
check expand

Key = RUNNER_TOKEN - or another name
Value = glpat-aKr-ibCNkmjims8YQguW - Personal Access Token which we have already got above

# include

Pipeline editor -> Full Configuration

It shows third party code from templates!

# debug

```yml
variables:
  CI_DEBUG_TRACE: 'true'
```

# template

Template is **.gitlab_ci.yml** file too. And it is in another repository or another instance ect.

We can **include** pipelines to each other.

```yml
include:
  local: smoke.gotlab-ci.yml
```

include remote for remote repository.
