# Variables

В каждом deploy одна и та же переменная ${DB_SERVER}

Settings -> CI/CD -> Variables expand
Add variable
Env = from pipeline, staging
No protect
No mask
Key is var name from pipeline
Value is value from our instance, like this
${DB_SERVER} = db-staging.domain.local

Create other var. It's similar to first, bur env = prod and protected yes, and
${DB_SERVER} = db-production.domain.local

Manual operation in pipeline must be run only manually. This job will not start automatically.

How to stop?
Operate -> Environments -> choose env -> stop

My Registry token called GITLAB_CI_USER is
gitlab+deploy-token-3696606
76ygCB6NodBojyY88R_d

It need for my login and password called
GITLAB_CI_USER
GITLAB_CI_PASSWORD
from my pipeline.
