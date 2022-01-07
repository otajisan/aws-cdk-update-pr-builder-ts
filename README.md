# aws-cdk-update-pr-builder-ts

Create a Pull Request for AWS CDK

## Usage

```yaml

```

## Action Inputs

| Name         | Required | Description                                                | Default |
|--------------|----------|------------------------------------------------------------|---------|
| node-version | false    | version of nodejs                                          | `16.x`  |
| token        | false    | Github Token (Like Personal Access Token)                  |         |
| base-branch  | false    | base branch when creating a Pull Request                   | `main`  |
| assignees    | false    | Pull Request Assignees (a comma or newline separated list) |         |
| reviewers    | false    | Pull Request Reviewers (a comma or newline separated list) |         |

## Action Outputs

- N/A

## Action behavior

- Use `ncu` to upgrade the package in your `package.json`
- Make a Pull Request towards the specified base branch (_Default:_ `main`)
- This action uses the following awsome Github Action for Pull Request Action.
    - https://github.com/peter-evans/create-pull-request