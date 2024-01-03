# FYI: Key pair in age.agekey or key.txt is strictly for testing purposes

1. install sops
2. install age
3. encrypt secret with ```sops -e -i $secret-file-name.yaml```
4. install yq

### Hooks
1. run init to setup local github pre-commit hook
2. update .sops.yaml to configure encryption behaviour [See Best Practice]
3. 

### Flux Integretion
1. Create flux Kustomization for secret management

##### Notes
- when using age or PGP make sure you set SOPS_AGE_KEY_FILE env to point to file that holds the keys


https://autrilla.gitbooks.io/sops/content/uage.html
https://github.com/getsops/sops
https://www.thorsten-hans.com/encrypt-your-kubernetes-secrets-with-mozilla-sops/
https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks
https://developer.harness.io/docs/continuous-delivery/gitops/use-gitops/sops/#use-age-or-pgp
https://medium.com/picus-security-engineering/manage-your-secrets-with-mozilla-sops-and-gitops-toolkit-flux-cd-v2-7aa98f626001
https://softwaremill.com/safe-storage-of-kubernetes-secrets-with-mozilla-sops-and-iac/
https://www.gitops.tech/#what-is-gitops
https://fluxcd.io/flux/guides/mozilla-sops/#optional-export-the-public-key-into-the-git-directory

#### filename_regex
Purpose: The filename_regex is used to match the name of the file itself, irrespective of its path or location in the directory structure.
Use-case: This is useful when you want to apply a specific encryption rule to files based on their filenames, regardless of where they are located.
Example: If you set filename_regex: '.*\.env$', it will match any file that ends with .env, such as config.env, production.env, etc., across all directories.
#### path_regex
Purpose: The path_regex matches the entire path of the file, including its directory structure.
Use-case: This is useful when you want to apply encryption rules based on the file's location in your project's directory structure.
Example: If you have a rule with path_regex: 'dev/.*\.yaml$', it will match YAML files that are in the dev directory (e.g., dev/config.yaml) but not those in other directories.
Key Differences
Scope of Matching:

filename_regex is for matching just the file's name.
path_regex is for matching the file's full path, including directories.
Flexibility and Specificity:

filename_regex is less specific and is ideal for applying a rule to a file type across the whole project.
path_regex provides more control and is suited for applying rules to files in specific locations.
