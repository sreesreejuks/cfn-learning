
# cfn-learning

This repository contains CloudFormation templates for learning purposes.


## Repository Structure


-   **`cfn-vpc-Setup/`**: This directory contains the CloudFormation template for setting up a Virtual Private Cloud (VPC) with public and private subnets.


    -   `cfn-vpc-setup.yml`: The CloudFormation template file.

## CloudFormation Template: `cfn-vpc-setup.yml`

This template creates a VPC with:

-   A configurable CIDR block for the VPC.
-   Three public subnets, each in a different Availability Zone.
-   Three private subnets, each in a different Availability Zone.
-   Enables DNS support and hostnames.
-   Tags all resources for easy identification.


## Parameters

The template accepts the following parameters:

| Parameter              | Description                                                                    | Default Value  |
| :--------------------- | :----------------------------------------------------------------------------- | :------------- |
| `VPCName`             | The name of the VPC.                                                           | `MyAWSVPC`     |
| `CIDRRange`           | The CIDR block for the VPC.                                                    | `10.0.0.0/16`  |
| `PublicSubnetCidrWebA` | CIDR block for the Public Web Subnet in Availability Zone A.                 | `10.0.1.0/24`  |
| `PublicSubnetCidrWebB` | CIDR block for the Public Web Subnet in Availability Zone B.                 | `10.0.2.0/24`  |
| `PublicSubnetCidrWebC` | CIDR block for the Public Web Subnet in Availability Zone C.                 | `10.0.3.0/24`  |
| `PrivateSubnetCidrAppA` | CIDR block for the Private App Subnet in Availability Zone A.                | `10.0.4.0/24`  |
| `PrivateSubnetCidrAppB` | CIDR block for the Private App Subnet in Availability Zone B.                | `10.0.5.0/24`  |
| `PrivateSubnetCidrAppC` | CIDR block for the Private App Subnet in Availability Zone C.                | `10.0.6.0/24`  |


## Deployment

To deploy this project run

    1.  Clone this repository to your local machine.
        ```bash
        git clone https://github.com/sreesreejuks/cfn-learning.git
        ```

    2.  Navigate to the `cfn-vpc-Setup` directory.
        ```bash
        cd cfn-learning/cfn-vpc-Setup
        ```
    3.  Use the AWS CLI, AWS Management Console, or other infrastructure-as-code tools to deploy the `cfn-vpc-setup.yml` template.
        ```bash
        aws cloudformation create-stack --stack-name <YOUR-STACK-NAME> --template-body file://cfn-vpc-setup.yml --parameters ParameterKey=VPCName,ParameterValue=<YOUR-VPC-NAME> ParameterKey=CIDRRange,ParameterValue=<YOUR-CIDR-RANGE> ...
        ```

        *Replace `<YOUR-STACK-NAME>`, `<YOUR-VPC-NAME>`, `<YOUR-CIDR-RANGE>` and other parameters with the desired values.*
## Features


-   The template uses `!GetAZs` function to automatically select availability zones for subnets.
-   The template allows for customization of the VPC name and CIDR blocks through the input parameters.
-   The public subnets are configured to automatically assign public IP addresses to instances launched in them (`MapPublicIpOnLaunch: true`).
-   The template includes a CIDR check to ensure valid IP ranges are input, and default values have been set for convenience.

## Documentation

[Documentation](https://linktodocumentation)


## Lessons Learned

What did you learn while building this project? What challenges did you face and how did you overcome them?

    "This project significantly improved my practical knowledge of CloudFormation. 
    I became more comfortable with the various sections of a template, handling parameters, 
    using intrinsic functions, creating VPC and subnet resources, and learned to 
    define a good template with user-friendly parameters and appropriate error validation."

### What I Learned:

    1. Understood the structure of CloudFormation templates and their core components.
    2. Learned how to create VPCs and public/private subnets, configuring key properties.
    3. Gained experience using parameters, intrinsic functions (!Ref, !Sub, !GetAZs, !Select), and outputs.
    4. Implemented CIDR validation and availability zone selection for flexibility.
    5. Added IPv6 support to the VPC
    6. Used Metadata to improve usability with parameter groups and labels.

### Challenges & Solutions:

    1. Challenge: Ensuring valid CIDR input. Solution: Used AllowedPattern and ConstraintDescription.
    2. Challenge: Hardcoded availability zones. Solution: Used !GetAZs and !Select for dynamic selection.
    3. Challenge: Debugging vague CloudFormation errors. Solution: Careful analysis of error messages and re-testing.
## Authors

- [@sreesreejuks](https://www.github.com/sreesreejuks)


## License

This project is licensed under the [MIT License](LICENSE).


## Contributing

Contributions are always welcome!



## Feedback

If you have any feedback or intrested in collaboration, please reach out to me at mail@sreesreejuks.com

