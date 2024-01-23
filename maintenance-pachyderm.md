
## Bringing fork up-to-date
Add the upstream repo as a remote origin (only need to do once):
```
git remote add upstream git@github.com:danielgtaylor/python-betterproto.git
```

Fetch any changes
```
git fetch upstream
```

Go through all the commit for which we are "behind" and cherry-pick the necessary commits
```
git cherry-pick <commit-sha>
```

We only need changes to the `compiler` portion of the codebase.
You should be looking out for changes under 
  `betterproto/compile` and `betterproto/plugin`.

To "test" the changes, push your branch to GitHub and update the
dependency here: https://github.com/pachyderm/pachyderm/blob/master/python-sdk/proto/Dockerfile.
You can use the following format for testing:
```
RUN python3 -m pip install 'betterproto[compiler] @ git+https://github.com/pachyderm/python-betterproto.git@<branch-name>
```

Once merged, you need to rebuild the package and publish as a GitHub release.
Then update the version of the dependency in the Dockerfile specified above.
