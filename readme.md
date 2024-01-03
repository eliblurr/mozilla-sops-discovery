# Mozilla SOPs discovery for integration with flux
This project is a playground for experimenting with Mozilla SOPs and Integration with Flux

#### FYI: Assymetric key pair in age.agekey or key.txt is strictly for testing purposes

**Document contents**

- [Prerequisite](#Prerequisite)
- [Setup](#setup)
- [Usage](#usage)
- [Environment Variables]()
- [Other Notes](#other-notes)
- [References](#references)

### Prerequisite
- Install [Mozilla SOPs](https://github.com/getsops/sops)
- Install [Age Encryption](https://github.com/FiloSottile/age)
- Install [Python](https://www.python.org/downloads/) if not available

### Setup
1. Clone the project
2. Change directory to project directory in your shell
```
cd /path/to/project/directory/
```
3. Set `SOPS_CONFIG_PATH` environment variable to point the absolute path of `.sops.yaml` file
4. Setup `git` hook by running the command below
```
./hooks/init
```
#### *Optionals*
5. If you are using age for encryption, generate asymmetric key pair with the command below:
```
age-keygen -o key.txt
```
6. Set `SOPS_AGE_KEY_FILE` environment variable to point the absolute path of generated asymmetric key pair.

### Usage
- Mozilla SOPs in this context will only work on file/path patterns specified in the `.sops.yaml` and apply encryptions based on any specified configuration in the file. This requires users to add confugurations for files or paths they want to encrypt.

### Environment Variables
| KEYWORDS | DESCRIPTION | DEFAULT VALUE | VALUE TYPE | IS REQUIRED | 
| :------: | :----: | :-----------: | :--------: | :---------: |
| SOPS_CONFIG_PATH | set to the asbolute value of `.sops.yaml`  | | string | yes |
| SOPS_AGE_KEY_FILE | set to the abosolute path of the generated key | | string | only when using age encryption |

### Other Notes
- When using age or PGP make sure you set `SOPS_AGE_KEY_FILE` env to point to file that holds the keys
- Ensure the `SOPS_CONFIG_PATH` environment variable is set.
- `filename_regex` key in `.sops.yaml` is used to match the name of the file itself, irrespective of its path or location in the directory structure.
- `path_regex` key in `.sops.yaml` matches the entire path of the file, including its directory structure.
- By default Mozilla SOPs will attempt to encrypt any file passed to it, the written hooks and script ensures only `path_regex` and `filename_regex` keys set in `.sops.yaml` pass for SOPs.
- `encrypted_regex` key in `.sops.yaml` specifies which keys values should be encrypted in files. 
- To apply a [Key Management Service(KMS)](https://www.fortanix.com/platform/data-security-manager/key-management-service), read more from [here](https://github.com/getsops/sops/blob/main/README.rst)
- Scripts in `hooks` directory are affected by the working directory they are called from, always run scripts from the projects roots directory 
- `init` script in `hooks` directory install pyyaml library.

### References
- [Official Mozilla SOPs Documentation](https://github.com/getsops/sops/blob/main/README.rst)
- https://autrilla.gitbooks.io/sops/content/uage.html
- https://github.com/getsops/sops
- https://www.thorsten-hans.com/encrypt-your-kubernetes-secrets-with-mozilla-sops/
- https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks
- https://developer.harness.io/docs/continuous-delivery/gitops/use-gitops/sops/#use-age-or-pgp
- https://medium.com/picus-security-engineering/manage-your-secrets-with-mozilla-sops-and-gitops-toolkit-flux-cd-v2-7aa98f626001
- https://softwaremill.com/safe-storage-of-kubernetes-secrets-with-mozilla-sops-and-iac/
- https://www.gitops.tech/#what-is-gitops
- https://fluxcd.io/flux/guides/mozilla-sops/#optional-export-the-public-key-into-the-git-directory
