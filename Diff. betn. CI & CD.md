# Continuous Integration (CI) and Continuous Delivery/Deployment (CD)

Continuous Integration (CI) and Continuous Delivery/Deployment (CD) are practices in software development that automate the processes of software testing, building, and deploying. Here's a simple explanation of their differences:

CI & CD -Continuous integrtion / continuous deliverY and continous deployment
- what is ci & cd?
- methodology
- automated
- 3)ci= Continuous build and continuous test
CI/  integration tools= jenkins,Bamboo(altasian), tranis CI,Build bot

## Continuous Integration (CI)

1. **Definition**: CI is the practice of automatically integrating code changes from multiple contributors into a shared repository several times a day.
2. **Purpose**: To ensure that the new code integrates smoothly with the existing codebase and to detect errors early.
3. **Process**:
   - Developers frequently commit code changes to a central repository.
   - Each commit triggers an automated build and test process.
   - If the build or tests fail, developers are notified immediately so they can fix the issue.
4. **Tools**: Jenkins, Travis CI, CircleCI, GitLab CI, etc.

## Continuous Delivery (CD)

1. **Definition**: CD is the practice of automatically preparing code changes for a release to production. It ensures that the codebase is always in a deployable state.
2. **Purpose**: To enable frequent and reliable releases of software to production with minimal manual intervention.
3. **Process**:
   - Builds on CI by adding automated deployment steps.
   - After passing automated tests in CI, the code is automatically prepared for deployment.
   - It might include additional automated tests and quality checks.
   - The deployment to production is a manual step, though everything is ready for it.
4. **Tools**: Jenkins, GitLab CI/CD, Spinnaker, Bamboo, etc.

## Continuous Deployment (CD)

1. **Definition**: Continuous Deployment extends Continuous Delivery by automatically deploying every change that passes the automated tests to production.
2. **Purpose**: To deploy changes to production as soon as they are ready, reducing the time to market and allowing for quick feedback and iteration.
3. **Process**:
   - Every change that passes through the CI pipeline and the automated tests in the CD pipeline is automatically deployed to production without manual intervention.
4. **Tools**: Jenkins, GitLab CI/CD, Spinnaker, Argo CD, etc.

## Key Differences

- **Automation**: CI focuses on automating the integration and testing of code. CD (both Continuous Delivery and Continuous Deployment) automates the release process, but Continuous Deployment takes it a step further by automating the deployment to production.
- **Manual Intervention**: In Continuous Delivery, the deployment to production is manual. In Continuous Deployment, the deployment to production is automatic.
- **Risk and Speed**: Continuous Deployment allows for rapid and frequent updates to production, which can be beneficial for quick feedback but requires a high level of confidence in the automated tests. Continuous Delivery provides a balance, ensuring the code is always ready to deploy but allowing for a final manual check before release.

## Summary

- **CI**: Integrate code frequently, run automated tests, catch issues early.
- **CD (Continuous Delivery)**: Ensure the code is always in a deployable state, but deploy to production manually.
- **CD (Continuous Deployment)**: Automatically deploy every change that passes automated tests to production.

These practices together help streamline the development process, improve code quality, and accelerate the delivery of new features and bug fixes.
