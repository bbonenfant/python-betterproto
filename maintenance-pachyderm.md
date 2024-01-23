
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

We only need changes to the `compiler` porition of the codebase.
You should be looking out for changes under 
  `betterproto/compile` and `betterproto/plugin`.

The final "test" is to rebuild the package and publish a GitHub release, then update the
dependency here: https://github.com/pachyderm/pachyderm/blob/master/python-sdk/proto/Dockerfile.
