# destroy-preview

Easily destroy an existing preview environment on the [Architect Cloud](https://www.architect.io/)

Suggestions and issues can be posted on the [issues page](https://github.com/architect-team/destroy-preview/issues).

[Inputs](#Inputs)
* [email](#email)
* [password](#password)
* [account](#account)
* [environment](#environment)
* [component_name](#component_name)

## Inputs

### `email`

**Required** Email used to log in to the Architect Cloud

### `password`

**Required** Password used to log in to the Architect Cloud

### `account`

**Required** Architect Cloud account for the registered component and the created environment

### `environment`

**Required** Name of the environment which will be created

### `component_name`

**Required** Name of the component to be registered

## Example usage

The following will be executed by the workflow job below:
* Log user into the Architect Cloud
* Remove the component with the name:tag combination `component_name`:`environment` from the environment specified which belongs to the account specified

```yaml
jobs:
  architect_destroy_preview:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/setup-node@v1
    - name: Destroy Preview
      uses: architect-team/destroy-preview@v1.0.0
      with:
        email: ${{ github.event.inputs.email }}
        password: ${{ secrets.PASSWORD }}
        account: ${{ github.event.inputs.account }}
        environment: ${{ github.event.inputs.environment }}
        component_name: ${{ github.event.inputs.component_name }}
```
