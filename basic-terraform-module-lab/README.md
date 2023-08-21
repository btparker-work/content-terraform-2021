# content-terraform-2021

# Commands
# Format the code in all of your files in preparation for deployment:

terraform fmt -recursive
# Initialize the Terraform configuration to fetch any required providers and get the code being referenced in the module block:

terraform init
# Validate the code to look for any errors in syntax, parameters, or attributes within Terraform resources that may prevent it from deploying correctly:

terraform validate
# You should receive a notification that the configuration is valid.

Review the actions that will be performed when you deploy the Terraform code:

terraform plan
# In this case, it will create 3 resources, which includes the EC2 instance configured in the root code and any resources configured in the module. If you scroll up and view the resources that will be created, any resource with module.vpc in the name will be created via the module code, such as module.vpc.aws_vpc.this.

# Deploy the code:

terraform apply --auto-approve
# Note: The --auto-approve flag will prevent Terraform from prompting you to enter yes explicitly before it deploys the code.

# Once the code has executed successfully, note in the output that 3 resources have been created and the private IP address of the EC2 instance is returned as was configured in the outputs.tf file in your main project code.

# View all of the resources that Terraform has created and is now tracking in the state file:

terraform state list
# The list of resources should include your EC2 instance, which was configured and created by the main Terraform code, and 3 resources with module.vpc in the name, which were # configured and created via the module code.

# Tear down the infrastructure you just created before moving on:

terraform destroy
# When prompted, type yes and press Enter.