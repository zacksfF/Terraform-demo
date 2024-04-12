## Terraform Config Files
#### Configuration File Syntax
The configuration file uses the same HCL syntax as `.tf` files, but with different attributes and blocks. The following example illustrates the general syntax; see the following section for information on the meaning of each of these settings
```
plugin_cache_dir   = "$HOME/.terraform.d/plugin-cache"
disable_checkpoint = true
```

#### Example
A simple Terraform example that describes a basic network topology for GCP, giving you a sense of the overall structure and syntax of the Terraform language:
```
provider "google" {
  project = "your_project_id"
  region  = "us-central1"
}

# Create a VPC network
resource "google_compute_network" "vpc" {
  name = "my-vpc-network"
  auto_create_subnetworks = false
}

# Create a subnet
resource "google_compute_subnetwork" "subnet" {
  name          = "my-vpc-subnet"
  region        = google_compute_network.vpc.region
  network       = google_compute_network.vpc.name
  ip_cidr_range = "10.1.0.0/16"
}
```
For more complex network configurations or using Terraform with other cloud providers, refer to the official Terraform documentation and provider guides: https://developer.hashicorp.com/terraform/tutorials