# ReactAdmin Enterprise Edition action

This action sets up your ReactAdmin Enterprise Edition authentication by creating a `.npmrc` file (or an `.yarnrc.yml` file if you use Yarn v2 or more) and adding your secret token that you can find on your [ReactAdmin Enterprise Edition setup page](https://registry.marmelab.com/setup) to use [private modules](https://marmelab.com/ra-enterprise/#private-modules).

## Environnement variable

### `RA_EE_CI_TOKEN`

You have to provide your ReactAdmin Enterprise Edition secret CI token. Do not paste it directly in your repository but use [Github Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) instead.

## Example usage

Create a file: `.github/workflows/ra-ee.yml`

```
name: ReactAdmin Enterprise Edition CI token Action
on: [push]

jobs:
  ra_enterprise_action_workflow:
    runs-on: ubuntu-latest
    name: Add ReactAdmin Enterprise Edition CI token
    steps:
      - uses: react-admin/ra-enterprise-action@1.0.0
        env:
          RA_EE_CI_TOKEN: ${{secrets.RA_EE_CI_TOKEN}}
```
