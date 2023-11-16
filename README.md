# Azure_GenerateBuildSuffix_UpdateBuildNumber
This template enables to generate a build suffix for the package version and to update the build number

## Pipeline Requirements

The dotNet Module pipeline requires the following parameters to be defined:

Parameters:

| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | :-------------: | :-------------: | :-------------: | :-------------: | ------------- |
| projects | Path to project(s) | String |  |  | Optional | Specifies Path to project(s) |
| suffix | Package version name | String |  |  | Required | Specifies Configuration of the package |

These parameters provide multiple use case options for the dotnet templates pipeline, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_GenerateBuildSuffix_UpdateBuildNumber
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: GenerateBuildSuffix.yaml
    parameters:
      suffix: '${{ parameters.suffix }}'

  - template: UpdateBuildNumber.yaml                    
  

        
  
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

  ```
