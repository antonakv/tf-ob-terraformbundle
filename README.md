# tf-ob-terraformbundle
Learn to use terraform-bundle to pack plugins

This manual is dedicated to 

## Requirements

- Hashicorp terraform recent version installed
[Terraform installation manual](https://learn.hashicorp.com/tutorials/terraform/install-cli)

- git installed
[Git installation manual](https://git-scm.com/download/mac)

## Preparation

- Clone git repository

```bash
git clone https://github.com/antonakv/tf-ob-terraformbundle.git
```

Example output:

```bash
Cloning into 'tf-ob-terraformbundle'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (12/12), done.
remote: Total 12 (delta 1), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (1/1), done.
```

- Change folder to tf-ob-terraformbundle

```bash
cd tf-ob-terraformbundle
```

- Run the `terraform providers mirror providersmirror` to create local mirror

Expected result:

```bash
% terraform providers mirror providersmirror
- Mirroring hashicorp/null...
  - Selected v3.1.1 to meet constraints ~> 3.1.1
  - Downloading package for darwin_amd64...
  - Package authenticated: signed by HashiCorp
- Mirroring hashicorp/random...
  - Selected v3.3.2 to meet constraints ~> 3.3.2
  - Downloading package for darwin_amd64...
  - Package authenticated: signed by HashiCorp
```

- Add mirror setting to the local terraform configuration file ~/.terraformrc

```bash
provider_installation {
  filesystem_mirror {
    path = "/Users/user/tf-ob-terraformbundle/providersmirror"
  }
}
```

- Run the `terraform init`

Expected result:

```bash
% terraform init    

Initializing the backend...

Initializing provider plugins...
- Finding hashicorp/null versions matching "~> 3.1.1"...
- Finding hashicorp/random versions matching "~> 3.3.2"...
- Installing hashicorp/null v3.1.1...
- Installed hashicorp/null v3.1.1 (unauthenticated)
- Installing hashicorp/random v3.3.2...
- Installed hashicorp/random v3.3.2 (unauthenticated)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```
