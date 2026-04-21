# TP Cloud Computing - Déploiement AWS

Déploiement de l'architecture du TP sur AWS avec Terraform, dans la région `eu-west-3`.

## Architecture

- VPC `10.0.0.0/16`
- Sous-réseau public `10.0.1.0/24` (AZ `eu-west-3a`)
- Internet Gateway + table de routage avec route par défaut vers l'IGW
- Security Group ouvrant SSH et HTTP
- Instance EC2 `web_server` de type `t3.micro` sous Ubuntu 22.04
- Nginx installé automatiquement au boot via `user_data`

## Prérequis

- Terraform installé
- Identifiants AWS configurés (via `aws configure` ou variables d'environnement
  `AWS_ACCESS_KEY_ID` / `AWS_SECRET_ACCESS_KEY`)

## Déploiement

```bash
cp terraform.tfvars.example terraform.tfvars
terraform init
terraform plan
terraform apply
```

L'URL du serveur web s'affiche à la fin du `apply`.

Pour tout supprimer : `terraform destroy`.
