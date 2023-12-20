# FYI: Key pair in key.txt is strictly for testing purposes

1. install sops
2. install age
3. encrypt secret with ```sops -e -i $secret-file-name.yaml```

### Hooks
1. run init to setup local github pre-commit hook
2. update .sops.yaml to configure encryption behaviour [See Best Practice]
3. 