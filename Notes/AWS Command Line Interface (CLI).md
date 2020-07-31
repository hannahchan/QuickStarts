# AWS Command Line Interface (CLI)

The AWS Command Line Interface (CLI) is the primary tool used to interact with AWS via the command line.

## Download and Install the AWS CLI

Download and install the appropriate package for your operating system from;

- https://aws.amazon.com/cli/

## Create an AWS IAM User

Before you can use the AWS CLI, you'll need to create a AWS Identity and Access Management (IAM) user for the AWS account you want to manage with _Programmatic_ access. This process generates an `Access Key ID` and a `Secret Access Key` which you'll need to later. For quick access to the AWS IAM console, use the link below.

- https://console.aws.amazon.com/iam/

## AWS Command Line (CLI) Reference

All AWS CLI commands start with aws. For a complete command line reference check out;

- https://awscli.amazonaws.com/v2/documentation/api/latest/index.html

## AWS Command Completion

On Unix-like systems, the AWS CLI includes a command-completion feature that enables you to use the TAB key to complete a partially typed command. For instruction on how to enable this feature, visit;

- https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-completion.html

## Managing AWS Credentials

AWS Credentials are store in profiles. To create or update the _default_ profile, use the command;

    aws configure

To create or update _named_ profiles, use the command;

    aws configure --profile <Named Profile>

AWS credentials are store in a text file located in the `.aws` sub-directory of a user's home directory.

## Specify AWS Credentials, Regions and Output Format

There are three ways to specify AWS Credentials, Regions and Output Format when using the AWS CLI.

### Default Profile

Use 'aws configure' to specify a default profile, region and output format **for every** console session.

### Session Profile

Set the appropriate environment variable to specify the default profile, region and output format for a particular console session.

- `AWS_PROFILE`
- `AWS_DEFAULT_REGION`
- `AWS_DEFAULT_OUTPUT`

For more information about environment variables that configure the AWS CLI, checkout;

- https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html

### Command

Add the `--profile`, `--region` or `--output` options to specify a profile, region or output format for a particular command. These options override the values provided by the default or session profile.

The output format can be either `json`, `text`, or `table`. If you don't specify an output format, `json` will be used.
