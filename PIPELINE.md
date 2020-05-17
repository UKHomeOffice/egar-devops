# CI/CD Pipeline


## High level overview
- Developer creates code change, signs it with GPG key and pushes to VCS
- Artifact is built and unit tested automatically 
- Upon successful tests outcome Developer creates Pull Request/Merge Request to SIT
- Code change is reviewed (built and tested locally according to PR description)
- Code change is approved by 2 junior members or 1 senior member of the team
- Code merge triggers build in SIT
- E2E tests are performed - if failed, code is reverted
- User Researcher requests tested code to be merged to UAT 
- User Acceptance Testing proceeds
- Upon successful UAT, Non-live Version of Production is created (Blue/Green)
- E2E production tests are performed on non-live version of Production
- Upon success Non-live becomes Live Production Environment
- Old Production is decommissioned

## Technology proposed
- VCS: GitHub/GitLab
- Build tool: Drone
- Artifact repository: Quay.io
- Deployment provider: Drone
- Deployment cluster: Kubernetes (ACP)
