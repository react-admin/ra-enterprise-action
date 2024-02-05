# React Admin Enterprise Edition action

This action sets up your package manager (`npm` or `yarn`) to use the [React Admin Enterprise Edition](https://marmelab.com/ra-enterprise/) private registry, which is required to download the [private modules](https://marmelab.com/ra-enterprise/#private-modules).

It works by creating a `.npmrc` file (or a `.yarnrc.yml` file if you use Yarn v2 or more) and adding the CI authentication token found on the [React Admin Enterprise Edition setup page](https://registry.marmelab.com/setup).

## Environnement variable

### `RA_EE_CI_TOKEN`

You need to provide your React Admin Enterprise Edition CI authentication token in the `RA_EE_CI_TOKEN` environment variable.

**Notice:** Do not paste it directly in your repository but use [Github Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) instead.

## Example usage

Create a file: `.github/workflows/ra-ee.yml`

```yml
name: React Admin Enterprise Edition CI token Action
on: [push]

jobs:
  ra_enterprise_action_workflow:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Add React Admin Enterprise Edition CI token
        uses: react-admin/ra-enterprise-action@1.0.0
        env:
          RA_EE_CI_TOKEN: ${{secrets.RA_EE_CI_TOKEN}}
      - name: NPM install
        run: npm install
```
