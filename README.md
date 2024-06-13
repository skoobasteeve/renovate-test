# 29629

Reproduction for [Renovate discussion 29629](https://github.com/renovatebot/renovate/discussions/29629).

## Current behavior

Renovate fails to look up Ansible Galaxy dependency DataDog.datadog, possibly due to the fact that [multiple results are returned during the API call](https://galaxy.ansible.com/api/v1/roles/?owner__username=DataDog&name=datadog). Other Ansible Galaxy roles like `geerlingguy.docker` do not have this issue.

```
DEBUG: Failed to look up galaxy package DataDog.datadog
{
  "dependency": "DataDog.datadog"
  "packageFile": "requirements.yml"
}

DEBUG: Found no satisfying versions with 'loose' versioning
DEBUG: Found no satisfying versions with 'docker' versioning
```

## Expected behavior

Renovate finds the role in Ansible Galaxy and opens a PR for the relevant updates. This is working correctly with `geerlingguy.docker` which I have configured in this repo.


```
DEBUG: 1 flattened updates found: geerlingguy.docker
```
