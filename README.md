### install client

brew tap hashicorp/tap
brew install hashicorp/tap/terraform


### create

mkdir learn-terraform-docker-container
cd learn-terraform-docker-container

In the working directory, create a file called main.tf and paste the following Terraform configuration into it.

```
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx"
  keep_locally = false
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "tutorial"

  ports {
    internal = 80
    external = 8000
  }
}


```

terraform init
terraform apply

docker ps

terraform destroy
