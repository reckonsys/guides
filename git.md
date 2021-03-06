# Git

Souce Code Management

## Pre-commit Hooks

We use [pre-commit](https://pre-commit.com/) framework to manage our hooks. Please be sure to run `pre-commit install` inside every single repo that you clone.

## Branching Model

In general, each repository will have 3 types of branches:

1. 1 `main` branch
2. 1 `dev` branch
3. Multiple `feat-*` or `fix-*` branches

```
main +------+----------------------------------------+----------> production
            |                               merge PR ^
            |                                        |
            |                                        |
        dev +--------+---------------------+---------+----------> staging / QA
                     |            merge PR ^
                     |                     |
                     |                     |
      feat-* / fix-* +---------------------+--------------------> dev / local
```

No commits will ever be made directly on `main`/ `dev` branches (except initial and merge commits)

The `main` branch will be deployed to the production environment. So this branch is well tested and is the most stable. The `main` branch will only accept PRs from the `dev` branch. Merges to the `main` branch should be thoroughly reviewed by tech leads.

The `dev` branch will be deployed to staging or QA environments. This is mostly a stable branch. The `dev` branches will accept PRs from any `feat-*` or `fix-*` branches.

The `feat-*` branches are created by developers working on specific features. feature branches are always created from the latest `dev` commit. The `fix-*` branches are created whenever a bug is found on the staging / QA / Production environment . Both `feat-*` and `fix-*` branches will always merge back into the `dev` branch. Both these kinds of branches can be deployed on-demand into the dev environment.


## Commit Messages

Messages should be max 50 chars long (including type and issue #). Every commit message MUST follow the following pattern:

```
<type>(<issue number>): <short summary>
  │       │                   │
  │       │                   └─⫸ Summary in present tense. Not capitalized. No period at the end.
  │       │
  │       └─⫸ Issue Number: the issue # (or `na` should be used whenever issue # is not applicable)
  │
  └─⫸ Commit Type: build|docs|feat|fix|perf|refac|test
```



##### Type

Must be one of the following:

* **build**: Changes to Dockerfile, poetry, package.json, requirements.txt, deployment manifest, etc
* **docs**: Documentation only changes
* **feat**: A new feature / completing a previously prototyped feature
* **fix**: A bug fix
* **perf**: A code change that improves performance
* **refac**: A code change that neither fixes a bug nor adds a feature
* **test**: Adding missing tests or correcting existing tests


##### Sample Commit Messages:

* feat(#12): user login and logout
* fix(#20): validate FooInput
* build(na): export requirements.txt
* refac(#43): optimize report query
