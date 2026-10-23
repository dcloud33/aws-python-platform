# AWS Python Platform

A project to build a repeatable AWS deployment platform for Python APIs using Terraform and CI/CD, with access controls, health checks, and deployment logs.

## Project status

**Planning stage.** The requirements and intended workflow are defined below. Application code, infrastructure, and deployment automation have not yet been implemented.

## Business problem

The development team needs a consistent way to deploy Python APIs to AWS. Different manual deployment steps create inconsistent environments, deployment mistakes, and unnecessary troubleshooting. The team needs a repeatable deployment process with security and cost controls.

## Intended users

Development-team members who need to deploy and test Python APIs on AWS through a documented workflow.

## Acceptance criteria

These are planned requirements. Each will be verified as the implementation progresses.

| Area | Required behavior | Verification |
| --- | --- | --- |
| Deployment | A developer can deploy a Python API to AWS using the documented workflow. | Follow the instructions and send an authorized request to the deployed API. |
| Consistency | Deployments follow the same automated steps using version-controlled configuration. | Repeat the workflow without undocumented manual changes. |
| Failed checks | Failed automated checks stop deployment and identify the failed step. | Introduce an error and confirm deployment stops with useful output. |
| Application health | After deployment, the workflow checks that the API responds as expected. | Verify an expected health response; confirm an unexpected response or timeout reports failure. |
| Access | Authorized development-team members can call the API; callers without permission are denied. | Test authorized and unauthorized requests. The automated health check must also have permission. |
| Teardown | The team can remove the test environment through a documented, repeatable process while retaining deployment logs. | Confirm intended resources are removed and retained logs remain accessible. |
| Log retention | Deployment logs remain available after teardown and are automatically deleted after 14 days. | Verify retention configuration and the log lifecycle. Retained storage may incur charges. |

## Intended deployment workflow

1. A developer pushes Python code to GitHub.
2. Automated code checks run.
3. If a check fails, the workflow stops and reports the error.
4. If all checks pass, the workflow deploys the application to AWS.
5. The workflow sends an authorized request to the API's health endpoint.
6. The expected response confirms success. An unexpected response or no response reports failure and provides logs for troubleshooting.
7. When testing is complete, the team tears down the test environment. Deployment logs remain available for 14 days.

A completed deployment does not guarantee a working application. The post-deployment health check verifies that the running API responds as expected.

## Planned technology

- **Python:** API implementation and automation where needed.
- **AWS:** application hosting and supporting services; specific services are still to be selected.
- **Terraform:** version-controlled infrastructure provisioning and teardown.
- **Docker:** reproducible application packaging.
- **CI/CD:** automated checks, deployment, and health verification; tooling is still to be selected.
- **Git and GitHub:** source control, documentation, and incremental delivery.

Hosting, authentication, log storage, and CI/CD implementation decisions will be documented as the design develops.

## First milestone

- [x] Define the business problem and intended users.
- [x] Define initial acceptance criteria and deployment workflow.
- [x] Create the GitHub repository and initial project documentation.
- [ ] Clone the repository to the development machine.
- [ ] Build the smallest Python API with a health endpoint.
- [ ] Run and verify the API locally.
- [ ] Add local setup and verification instructions.

## Working approach

Each feature progresses through requirements, design or pseudocode, implementation, verification, and documentation. Commits will record incremental progress. Setup instructions, architecture decisions, troubleshooting notes, and verification evidence will be added as working capabilities are delivered.
