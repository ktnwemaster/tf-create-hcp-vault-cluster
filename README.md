# tf-create-hcp-vault-cluster
# tfc-create-hcp-vault-cluster

# HCP Vault Cluster Setup

This Terraform configuration sets up a HashiCorp Cloud Platform (HCP) Vault cluster within an existing HashiCorp Virtual Network (HVN). It consists of three main resources:

## Resources

1. **HCP HVN (`hcp_hvn`)**:
   - **Purpose**: This resource references an existing HashiCorp Virtual Network (HVN) where the Vault cluster will be deployed.
   - **Parameters**:
     - `hvn_id`: The ID of the HVN where the Vault cluster will reside.
     - `cloud_provider`: The cloud provider (e.g., AWS, Azure) used for the HVN.
     - `region`: The geographical region where the HVN is located.
     - `cidr_block`: The CIDR block associated with the HVN.

2. **HCP Vault Cluster (`hcp_vault_cluster`)**:
   - **Purpose**: Deploys a Vault cluster within the specified HVN.
   - **Parameters**:
     - `cluster_id`: A unique identifier for the Vault cluster.
     - `hvn_id`: The ID of the HVN where the Vault cluster will be hosted.
     - `tier`: Specifies the tier type of the Vault cluster (e.g., Development, Production).
     - `public_endpoint`: Enables public access to the Vault cluster.

3. **HCP Vault Cluster Admin Token (`hcp_vault_cluster_admin_token`)**:
   - **Purpose**: Generates an admin token for the newly created Vault cluster.
   - **Parameters**:
     - `cluster_id`: The ID of the Vault cluster for which the admin token will be generated.

## Usage

To deploy this configuration, ensure you have the necessary variables set (`vault_hvn`, `cloud_provider`, `region`, `cluster_cidr`, `vault_cluster_id`, and `tier_type`), and then run the Terraform commands:

\`\`\`bash
terraform init
terraform apply
\`\`\`

This will set up the Vault cluster within your specified HVN and provide you with an admin token to manage the cluster.

## Prerequisites

- An existing HCP account with the necessary permissions.
- A pre-configured HVN in HCP.
- Terraform installed on your local machine.

## Outputs

- **Admin Token**: The admin token generated by the `hcp_vault_cluster_admin_token` resource will be essential for managing the Vault cluster.