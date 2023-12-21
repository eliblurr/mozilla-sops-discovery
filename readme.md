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