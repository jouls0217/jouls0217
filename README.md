# jouls0217

`aws` · `terraform` · `kubernetes` · `github-actions`

I build and maintain the infrastructure and delivery pipelines that production workloads run on.

---

### 🧠 `main.tf`

```hcl
resource "engineer" "jouls" {
  role  = "DevOps Engineer"
  cloud = "aws"

  focus = [
    "infrastructure as code",
    "ci/cd pipelines",
    "container platforms",
    "cost visibility",
  ]

  optimizes_for = "reproducible, reviewable, boring to operate"

  lifecycle {
    prevent_destroy = true
  }
}
```

> If it can't be described in code and rolled back, it isn't done.

---

### ☁️ `providers.tf`

```hcl
locals {
  # multiple AWS regions, each with its own state backend
  regions      = ["primary", "secondary"]
  environments = ["uat", "staging", "prod"]

  # separate state, separate credentials, separate blast radius
  isolation = "per-region, per-environment"
}
```

---

### 🔀 `moved.tf`

```hcl
# development is where I came from; infrastructure is where I work
moved {
  from = module.developer
  to   = module.devops
}
```

---

### 📦 `modules.tf`

#### `module "cloud"`

![AWS](https://img.shields.io/badge/AWS-%23232F3E.svg?style=for-the-badge&logo=amazon-web-services&logoColor=FF9900)
![Amazon EKS](https://img.shields.io/badge/Amazon%20EKS-FF9900?style=for-the-badge&logo=amazon-eks&logoColor=white)
![Amazon ECR](https://img.shields.io/badge/Amazon%20ECR-FF9900?style=for-the-badge&logo=amazon-ecs&logoColor=white)
![Amazon EC2](https://img.shields.io/badge/Amazon%20EC2-FF9900?style=for-the-badge&logo=amazon-ec2&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=for-the-badge&logo=amazon-s3&logoColor=white)
![Amazon RDS](https://img.shields.io/badge/Amazon%20RDS-527FFF?style=for-the-badge&logo=amazon-rds&logoColor=white)
![Amazon VPC](https://img.shields.io/badge/Amazon%20VPC-%23FF9900.svg?style=for-the-badge&logo=amazon-web-services&logoColor=white)
![AWS IAM](https://img.shields.io/badge/IAM-%23DD344C.svg?style=for-the-badge&logo=amazon-web-services&logoColor=white)
![Route 53](https://img.shields.io/badge/Route%2053-%238C4FFF.svg?style=for-the-badge&logo=amazon-route-53&logoColor=white)
![Amazon CloudWatch](https://img.shields.io/badge/CloudWatch-FF4F8B?style=for-the-badge&logo=amazon-cloudwatch&logoColor=white)
![AWS Cost Explorer](https://img.shields.io/badge/Cost%20Explorer-%23FF9900.svg?style=for-the-badge&logo=amazon-web-services&logoColor=white)

#### `module "iac"`

![Terraform](https://img.shields.io/badge/Terraform-%235835CC.svg?style=for-the-badge&logo=terraform&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)
![YAML](https://img.shields.io/badge/YAML-%23CB171E.svg?style=for-the-badge&logo=yaml&logoColor=white)

#### `module "ci_cd"`

![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Git](https://img.shields.io/badge/Git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![Shell Script](https://img.shields.io/badge/Shell_Script-%23121011.svg?style=for-the-badge&logo=gnu-bash&logoColor=white)
![Python](https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

#### `module "runtime"`

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-%23326CE5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

#### `module "data"`

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

---

### 🧪 `side_projects.tf`

```hcl
locals {
  hobbies = {
    odoo = ["python", "postgresql", "qweb", "xml"]
    mern = ["mongodb", "express", "react", "node"]
  }
}

# created only when capacity allows — never on the critical path
resource "side_project" "hobby" {
  for_each = var.free_time > 0 ? local.hobbies : {}

  name  = each.key
  stack = each.value
}
```

Development is a hobby and the occasional side gig these days — but it's still how I understand what I'm deploying.

---

```console
$ terraform apply

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
```
