We take new_pullreq.csv (2.2gb) as a source of PRs from which we derive a set of projects (together with projects from organization.csv and historical_projects.csv, which we abandon later).
fetcher.py is used to fetch a list of PRs together with modified files from github using GraphQL, paginated for the first 100 items.
The results are saved in cached folder (564mb).

miner.py used reviewed.csv to run refactoringminer
refactoringminer is a patched version that takes content diff for the whole PR instead of processing every commit in the PR in order to skip merge/rebase commits as well as multiple commits being the part of the same refactoring.
refminer-mvn-plugin is a maven plugin to run own patched version of refactoringminer.
combine_sources.py imports manually assessed PRs from google docs.
