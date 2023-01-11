# tag-exists-action
A GitHub action that determines if a tag exists in your repo.

## Inputs

### `tag`

**Required** The tag to search for.

## Outputs

### `exists`

A **string** value: `"true"` | `"false"`

## Example usage

```yaml
- uses: mukunku/tag-exists-action@v1.2.0
  id: checkTag
  with: 
    tag: "tag-to-search-for" # e.g: "v1.2.0"

- run: echo ${{ steps.checkTag.outputs.exists }}

- name: Conditionnally run a step if tag exists
  if: ${{ steps.checkTag.outputs.exists == 'true' }}
  run: |
    # Do something

- name: Conditionnally run a step if tag does NOT exists
  if: ${{ steps.checkTag.outputs.exists == 'false' }}
  run: |
    # Do something else
```

This action uses the `${{github.token}}` secret to automatically inject your access token. If you'd like to provide your own token instead check out [this help article](https://github.com/mukunku/tag-exists-action/wiki/Setting-the-GITHUB_TOKEN-explicitly).

### Community examples

Here are some use case examples from the community:

- [Dynamically update or recreate a GitHub Release](https://github.com/UnlyEd/github-action-await-vercel/blob/e6fd49bc8b6699fde54a52a13e4ff6e8bf7d9886/.github/workflows/auto-git-release-production.yml#L98-L130)
