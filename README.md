# Apache Airflow application stack for Kubernetes on Wodby

Deploy Apache Airflow with your own DAGs, plugins and Python packages on
Kubernetes with Wodby: your Git repository holds them, and Wodby builds Airflow
with them.

This repository defines the Wodby stack manifests and default service
composition for Apache Airflow.

<!-- wodby:generated:start -->

## Stack contract

- [Apache Airflow stack on Wodby](https://wodby.com/stacks/airflow)
- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Apache Airflow stack guide](https://wodby.com/docs/2.0/stacks/catalog/airflow/)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Service definitions

- [Apache Airflow service](https://github.com/wodby/service-airflow)
- [PostgreSQL service](https://github.com/wodby/service-postgres)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Apache Airflow<br>`airflow` | required; enabled by default; volumes: `data` 10 GB; links: `postgres` → `postgres` |
| PostgreSQL<br>`postgres` | required; enabled by default; volumes: `data` 20 GB |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Deploy this stack

Connect a Git repository started from the
[Airflow boilerplate](https://github.com/wodby/airflow-boilerplate):

- `dags/` holds your DAGs and `plugins/` your plugins.
- `requirements.txt` lists the Python packages they need, such as providers.

Choose the Airflow version when you create the app. The build starts from the
official `apache/airflow` image of that version and adds your code and packages;
the API server, scheduler, DAG processor, triggerer and setup step all run the
result.

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.
