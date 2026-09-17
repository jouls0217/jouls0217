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

```hcl
module "cloud" {
  source = "./modules/aws"

  services = [
    "eks", "ecr", "ec2", "s3", "rds",
    "vpc", "iam", "route53", "cloudwatch", "cost-explorer",
  ]
}

module "iac" {
  source = "./modules/iac"

  tools = ["terraform", "helm", "yaml"]
}

module "ci_cd" {
  source = "./modules/ci-cd"

  tools = ["github-actions", "git", "bash", "python"]
}

module "runtime" {
  source = "./modules/runtime"

  tools = ["docker", "kubernetes", "nginx", "linux"]
}

module "data" {
  source = "./modules/data"

  engines = ["postgresql", "mongodb", "mysql"]
}
```

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
