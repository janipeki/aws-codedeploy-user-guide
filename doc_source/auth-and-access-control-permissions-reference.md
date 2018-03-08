# AWS CodeDeploy Permissions Reference<a name="auth-and-access-control-permissions-reference"></a>

When you are setting up [Access Control](auth-and-access-control.md#access-control) and writing permissions policies that you can attach to an IAM identity \(identity\-based policies\), you can use the following table as a reference\. The table lists each AWS CodeDeploy API operation, the corresponding actions for which you can grant permissions to perform the action, and the format of the resource ARN to use for granting permissions\. You specify the actions in the policy's `Action` field, and you specify an ARN, with or without a wildcard character \(\*\), as the resource value in the policy's `Resource` field\.

You can use AWS\-wide condition keys in your AWS CodeDeploy policies to express conditions\. For a complete list of AWS\-wide keys, see [Available Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\.

To specify an action, use the `codedeploy:` prefix followed by the API operation name \(for example, `codedeploy:GetApplication` and `codedeploy:CreateApplication`\. To specify multiple actions in a single statement, separate them with commas \(for example, `"Action": ["codedeploy:action1", "codedeploy:action2"]`\)\.

**Using Wildcard Characters**

You can use a wildcard character \(\*\) in your ARN to specify multiple actions or resources\. For example, `codedeploy:*` specifies all AWS CodeDeploy actions and `codedeploy:Get*` specifies all AWS CodeDeploy actions that begin with the word `Get`\. The following example grants access to all deployment groups with names that begin with `West` and are associated with applications that have names beginning with `Test`\. 

```
arn:aws:codedeploy:us-west-2:80398EXAMPLE:deploymentgroup:Test*/West*
```

You can use wildcards with the following resources listed in the table:

+ *application\-name*

+ *deployment\-group\-name*

+ *deployment\-configuration\-name*

+ *instance\-ID*

Wildcards can't be used with *region* or *account\-id*\. For more information about wildcards, see [IAM Identifiers](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html) in *IAM User Guide*\. 

The actions you can specify in an IAM policy for use with AWS CodeDeploy are listed below\.

If you see an expand arrow \(**↗**\) in the upper\-right corner of the table, you can open the table in a new window\. To close the window, choose the close button \(**X**\) in the lower\-right corner\.


**AWS CodeDeploy API Operations and Required Permissions for Actions**  

| AWS CodeDeploy API Operations | Required Permissions \(API Actions\) | Resources | 
| --- | --- | --- | 
|  [AddTagsToOnPremisesInstances](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_AddTagsToOnPremisesInstances.html)  |  `codedeploy:AddTagsToOnPremisesInstances` Required to add tags to one or more on\-premises instances\.  |  arn:aws:codedeploy:*region*:*account\-id*:instance/*instance\-ID*  | 
|  [BatchGetApplicationRevisions](http://docs.aws.amazon.com/codedeploy/latest/APIReference/BatchGetApplicationRevisions.html)  |  `codedeploy:BatchGetApplicationRevisions` Required to get information about multiple application revisions associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:*application\-name*  | 
|  [BatchGetApplications](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetApplications.html)  |  `codedeploy:BatchGetApplications` Required to get information about multiple applications associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:\*  | 
| [BatchGetDeploymentGroups](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetDeploymentGroups.html) |  `codedeploy:BatchGetDeploymentGroups` Required to get information about multiple deployment groups associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
| [BatchGetDeploymentInstances](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetDeploymentInstances.html) | codedeploy:BatchGetDeploymentInstancesRequired to get information about one or more instance that are part of a deployment group\. |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [BatchGetDeployments](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetDeployments.html)  |  `codedeploy:BatchGetDeployments` Required to get information about multiple deployments associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [BatchGetOnPremisesInstances](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetOnPremisesInstances.html)  |  `codedeploy:BatchGetOnPremisesInstances` Required to get information about one or more on\-premises instances\.  |  arn:aws:codedeploy:*region*:*account\-id*:\*  | 
|  [ContinueDeployment](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ContinueDeployment.html)  |  `codedeploy:ContinueDeployment` Required during a blue/green deployment to start the process of registering instances in a replacement environment with an Elastic Load Balancing load balancer\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [CreateApplication](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateApplication.html)  |  `codedeploy:CreateApplication` Required to create an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:*application\-name*  | 
|  [CreateDeployment](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateDeployment.html) ¹  |  `codedeploy:CreateDeployment` Required to create a deployment for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [CreateDeploymentConfig](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateDeploymentConfig.html)  |  `codedeploy:CreateDeploymentConfig` Required to create a custom deployment configuration associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentconfig/*deployment\-configuration\-name*   | 
|  [CreateDeploymentGroup](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateDeploymentGroup.html)  |  `codedeploy:CreateDeploymentGroup` Required to create a deployment group for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [DeleteApplication](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeleteApplication.html)  |  `codedeploy:DeleteApplication` Required to delete an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:*application\-name*  | 
|  [DeleteDeploymentConfig](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeleteDeploymentConfig.html)  |  `codedeploy:DeleteDeploymentConfig` Required to delete a custom deployment configuration associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentconfig/*deployment\-configuration\-name*   | 
|  [DeleteDeploymentGroup](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeleteDeploymentGroup.html)  |  `codedeploy:DeleteDeploymentGroup` Required to delete a deployment group for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [DeregisterOnPremisesInstance](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeregisterOnPremisesInstance.html)  |  `codedeploy:DeregisterOnPremisesInstance` Required to deregister an on\-premises instance\.  |  arn:aws:codedeploy:*region*:*account\-id*:instance/*instance\-ID*  | 
|  [GetApplication](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetApplication.html)  |  `codedeploy:GetApplication` Required to get information about a single application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:*application\-name*  | 
|  [GetApplicationRevision](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetApplicationRevision.html)  |  `codedeploy:GetApplicationRevision` Required to get information about a single application revision for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:*application\-name*  | 
|  [GetDeployment](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeployment.html)  |  `codedeploy:GetDeployment` Required to get information about a single deployment to a deployment group for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [GetDeploymentConfig](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeploymentConfig.html)  |  `codedeploy:GetDeploymentConfig` Required to get information about a single deployment configuration associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentconfig/*deployment\-configuration\-name*   | 
|  [GetDeploymentGroup](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeploymentGroup.html)  |  `codedeploy:GetDeploymentGroup` Required to get information about a single deployment group for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [GetDeploymentInstance](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeploymentInstance.html)  |  `codedeploy:GetDeploymentInstance` Required to get information about a single instance in a deployment associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [GetOnPremisesInstance](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetOnPremisesInstance.html)  |  `codedeploy:GetOnPremisesInstance` Required to get information about a single on\-premises instance\.  |  arn:aws:codedeploy:*region*:*account\-id*:instance/*instance\-ID*  | 
|  [ListApplicationRevisions](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListApplicationRevisions.html)  |  `codedeploy:ListApplicationRevisions` Required to get information about all application revisions for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:\*  | 
|  [ListApplications](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListApplications.html)  |  `codedeploy:ListApplications` Required to get information about all applications associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:\*  | 
|  [ListDeploymentConfigs](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeploymentConfigs.html)  |  `codedeploy:ListDeploymentConfigs` Required to get information about all deployment configurations associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentconfig/\*  | 
|  [ListDeploymentGroups](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeploymentGroups.html)  |  `codedeploy:ListDeploymentGroups` Required to get information about all deployment groups for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/\*  | 
|  [ListDeploymentInstances](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeploymentInstances.html)  |  `codedeploy:ListDeploymentInstances` Required to get information about all instances in a deployment associated with the IAM user or AWS account\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [ListDeployments](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeployments.html)  |  `codedeploy:ListDeployments` Required to get information about all deployments to a deployment group associated with the IAM user, or to get all deployments associated with the IAM user or AWS account\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [ListGitHubAccountTokenNames](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListGitHubAccountTokenNames.html)  |  `codedeploy:ListGitHubAccountTokenNames` Required to get a list of the names of stored connections to GitHub accounts\.   |  arn:aws:codedeploy:*region*:*account\-id*:\*  | 
|  [ListOnPremisesInstances](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListOnPremisesInstances.html)  |  `codedeploy:ListOnPremisesInstances` Required to get a list of one or more on\-premises instance names\.  |  arn:aws:codedeploy:*region*:*account\-id*:\*  | 
|   PutLifecycleEventHookExecutionStatus  |  `codedeploy:PutLifecycleEventHookExecutionStatus` Required to provide notification of the status of the execution of a lifecycle hook event\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [RegisterApplicationRevision](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_RegisterApplicationRevision.html)  |  `codedeploy:RegisterApplicationRevision` Required to register information about an application revision for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:*application\-name*  | 
|  [RegisterOnPremisesInstance](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_RegisterOnPremisesInstance.html)  |  `codedeploy:RegisterOnPremisesInstance` Required to register an on\-premises instance with AWS CodeDeploy\.  |  arn:aws:codedeploy:*region*:*account\-id*:instance/*instance\-ID*  | 
|  [RemoveTagsFromOnPremisesInstances](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_RemoveTagsFromOnPremisesInstances.html)  |  `codedeploy:RemoveTagsFromOnPremisesInstances` Required to remove tags from one or more on\-premises instances\.  |  arn:aws:codedeploy:*region*:*account\-id*:instance/*instance\-ID*  | 
|  [SkipWaitTimeForInstanceTermination](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_SkipWaitTimeForInstanceTermination.html)  |  `codedeploy:SkipWaitTimeForInstanceTermination` Required in a blue/green deployment to override a specified wait time and start terminating instances in the original environment immediately\.  |  arn:aws:codedeploy:*region*:*account\-id*:instance/*instance\-ID*  | 
|  [StopDeployment](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_StopDeployment.html)  |  `codedeploy:StopDeployment` Required to stop an in\-progress deployment to a deployment group for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  [UpdateApplication](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_UpdateApplication.html) ³  |  `codedeploy:UpdateApplication` Required to change information about an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:application:*application\-name*  | 
|  [UpdateDeploymentGroup](http://docs.aws.amazon.com/codedeploy/latest/APIReference/API_UpdateDeploymentGroup.html) ³  |  `codedeploy:UpdateDeploymentGroup` Required to change information about a single deployment group for an application associated with the IAM user\.  |  arn:aws:codedeploy:*region*:*account\-id*:deploymentgroup:*application\-name*/*deployment\-group\-name*  | 
|  ¹ When you specify CreateDeployment permissions, you must also specify GetDeploymentConfig permissions for the deployment configuration and GetApplicationRevision or RegisterApplicationRevision permissions for the application revision\.  ² Valid for ListDeployments when providing a specific deployment group, but not when listing all of the deployments associated with the IAM user\) ³ For UpdateApplication, you must have UpdateApplication permissions for both the old application name and the new application name\. For UpdateDeploymentGroup actions that involve changing a deployment group's name, you must have UpdateDeploymentGroup permissions for both the old and new deployment group name\.   | 