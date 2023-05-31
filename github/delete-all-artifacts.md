# How to delete all artifacts from Github repository 

- create personal access token with `repo` scope
- run until $artifacts_response contains empty list, (sometime each delete request throws header status: 500)

```bash 
#!/bin/bash

# set the repository name and owner
repo_owner="<OWNER>"
repo_name="<REPO NAME>"


# set the base URL for the GitHub API
api_base_url="https://api.github.com"

# set the PAT as an environment variable
GITHUB_TOKEN="ghp_<PERSONAL ACCESS TOKEN>"

# get a list of artifacts for the repository
artifacts_url="$api_base_url/repos/$repo_owner/$repo_name/actions/artifacts"
artifacts_response=$(curl -sS -H "Accept: application/vnd.github+json" -H "Authorization: Bearer $GITHUB_TOKEN" -H "X-GitHub-Api-Version: 2022-11-28" "$artifacts_url")

echo $artifacts_response
artifact_ids=$(echo "$artifacts_response" | jq '.artifacts[].id')

# loop through the artifacts and delete each one
for artifact_id in $artifact_ids; do
delete_url="$api_base_url/repos/$repo_owner/$repo_name/actions/artifacts/$artifact_id"
echo $delete_url
echo $(curl -v -L -X DELETE -H "Accept: application/vnd.github+json" -H "Authorization: Bearer $GITHUB_TOKEN" -H "X-GitHub-Api-Version: 2022-11-28" "$delete_url")
done
```
