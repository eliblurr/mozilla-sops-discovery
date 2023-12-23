# FYI: Key pair in age.agekey or key.txt is strictly for testing purposes

1. install sops
2. install age
3. encrypt secret with ```sops -e -i $secret-file-name.yaml```

### Hooks
1. run init to setup local github pre-commit hook
2. update .sops.yaml to configure encryption behaviour [See Best Practice]
3. 

### Flux Integretion
1. Create flux Kustomization for secret management

https://autrilla.gitbooks.io/sops/content/uage.html
https://github.com/getsops/sops
https://www.thorsten-hans.com/encrypt-your-kubernetes-secrets-with-mozilla-sops/
https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks
https://developer.harness.io/docs/continuous-delivery/gitops/use-gitops/sops/#use-age-or-pgp
https://medium.com/picus-security-engineering/manage-your-secrets-with-mozilla-sops-and-gitops-toolkit-flux-cd-v2-7aa98f626001
https://softwaremill.com/safe-storage-of-kubernetes-secrets-with-mozilla-sops-and-iac/
https://www.gitops.tech/#what-is-gitops
https://fluxcd.io/flux/guides/mozilla-sops/#optional-export-the-public-key-into-the-git-directory