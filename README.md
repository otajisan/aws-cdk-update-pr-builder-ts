# aws-cdk-update-pr-builder-ts

Create a Pull Request for AWS CDK

![image](https://user-images.githubusercontent.com/5608492/148499646-bac49eaa-906f-446b-b410-76ab092d41f1.png)


## Usage

- Define the following workflow in the repository that uses _[AWS CDK](https://aws.amazon.com/cdk/)_ (Typescript).
  - `.github/workflows/create-aws-cdk-update-pr.yml`

```yaml
name: "Create PR to update AWS CDK"

on:
  push:
    branches:
      - main

jobs:
  create-aws-cdk-update-pr:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v1
      - name: Create AWS CDK Update PR
        uses: otajisan/aws-cdk-update-pr-builder-ts@v0.0.4
        with:
          token: ${{ secrets.CR_PAT }} # Github Personal Access Token
          assignees: otajisan
          reviewers: otajisan

```

## Action Inputs

| Name         | Required | Description                                                | Default |
|--------------|----------|------------------------------------------------------------|---------|
| token        | true     | Github Token (Like Personal Access Token)                  |         |
| node-version | false    | version of nodejs                                          | `16.x`  |
| base-branch  | false    | base branch when creating a Pull Request                   | `main`  |
| assignees    | false    | Pull Request Assignees (a comma or newline separated list) |         |
| reviewers    | false    | Pull Request Reviewers (a comma or newline separated list) |         |

## Action Outputs

- N/A

## Action behavior

- Use `ncu` to upgrade the package in your `package.json`

```bash
Run ncu -u
  ncu -u
  shell: /usr/bin/sh -e {0}
Upgrading /home/runner/work/eks-cdk/eks-cdk/package.json


 @aws-cdk/core     ^1.137.0  →  ^1.138.0     
 @aws-cdk/assert      2.3.0  →     2.4.0     
 @aws-cdk/aws-ec2  ^1.137.0  →  ^1.138.0     
 @aws-cdk/aws-eks  ^1.137.0  →  ^1.138.0     
 @aws-cdk/aws-iam  ^1.137.0  →  ^1.138.0     
 @types/node         17.0.7  →    17.0.8     
 aws-cdk              2.3.0  →     2.4.0     
```

- Make a Pull Request towards the specified base branch (_Default:_ `main`)
- This action uses the following awsome Github Action for Pull Request Action.
    - https://github.com/peter-evans/create-pull-request
- And then try `npm run build` and comment build result to created PR.

![image](https://user-images.githubusercontent.com/5608492/148499669-8b291b93-1c8c-4371-b4ff-97db0f429322.png)

# LICENSE
- [MIT](https://github.com/otajisan/aws-cdk-update-pr-builder-ts/blob/main/LICENSE)
