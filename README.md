# framework-version
This repo contains a JSON map of services in the framework stack to their semantic versions.
This repo is itself semantically versioned, yielding a single semantic version number for the whole stack.

Versions of the stack can be deployed to environments from the [deliverybot dashboard](https://app.deliverybot.dev/DataBiosphere/framework-version/branch/master).


## GitHub Actions Workflows
### update.yml
- Triggered on receiving a `version-bump` dispatch from a service repo.
- Bumps a service's version in `version.json` as specified by the dispatch payload, and commits the change to master

### tag.yml
- Triggered on JSON changes in master
- Bumps the version of the repo and tags the commit accordingly

### deploy.yml
- Triggered by deploying a stack version to an environment from the [deliverybot dashboard](https://app.deliverybot.dev/DataBiosphere/framework-version/branch/master)
- Sends a dispatch to the [framework-env repo](https://github.com/DataBiosphere/framework-env) containing the information of what environment needs to be updated to what stack version.
