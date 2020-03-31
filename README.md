## Description

`jaloc` is just another laptop on the cloud;
it collects some ideas to design your devops things.

## Deploy from a fixed tag

A popular way is to deploy from a specific tag or branch.
Normally you do as following

```
$ git tag  v1.0.2
$ git push v1.0.2
$ circleci --please --deploy --my-tag "v1.0.2"

$ git checkout -b my-qa-branch
$ circleci --please --deploy --my-branch "my-qa-branch"
```

What's happening here? When you look at your git history, you don't
know where your deployment point is. You have to learn your branches.

Let's do this

```
$ git tag production-ready -f
$ circleci --please --deploy --my-tag "production-ready"
```

This way helps

1. You learn the deployment point from git history (`git tag`).
2. It's easy to convert your deployment script to a poll/pull-based
   deployment script.
3. It's very easy to move your deployment to a different point
   by overriding the tag (`production-ready`).

Deployment tag works like a pointer and it can be resolved to arbitary
commit in your repository.

There may be some problems

1. It's easier to make mistake (wrong tag!)
2. If anyone can push tag, that would cause a lot of headache ^^
