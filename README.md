# Docker-in-Docker for GitLab CI

Docker-in-Docker for gitlab-ci-multi-runner Docker executor based on [jpetazzo/dind](https://github.com/jpetazzo/dind).

## Usage

### Just register the runner

```bash
gitlab-ci-multi-runner register \
                     --non-interactive \
                     --url "https://your.gitlabci.domain/" \
                     --registration-token "REGISTRATION_TOKEN" \
                     --description "gitlab-ci-dind-runner" \
                     --executor "docker" \
                     --docker-image "orih/dind:latest" \
                     --docker-privileged true
```

### Or, build by yourself and use it

```bash
cd /path/to/repos
docker build -t YOUR_REPOS/dind:latest .
docker push YOUR_REPOS/dind:latest

gitlab-ci-multi-runner register \
                     --non-interactive \
                     --url "https://your.gitlabci.domain/" \
                     --registration-token "REGISTRATION_TOKEN" \
                     --description "gitlab-ci-dind-runner" \
                     --executor "docker" \
                     --docker-image "YOUR_REPOS/dind:latest" \
                     --docker-privileged true
```

# License

Copyright (c) 2013 [Jérôme Petazzoni](https://github.com/jpetazzo)  
Copyright (c) 2015 [Orih](https://github.com/orih)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
