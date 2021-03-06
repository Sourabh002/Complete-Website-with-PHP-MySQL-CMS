Azure_AppService_AuthZ_Grant_Min_RBAC_Access 	 | 	 All users/identities must be granted minimum required permissions using Role Based Access Control (RBAC) 	 | 	 Remove any excessive privileges granted on the App Service. Run command: Remove-AzRoleAssignment -SignInName '<SignInName>' -Scope '<Scope>' RoleDefinitionName '<RoleDefinitionName>'. Run 'Get-Help Remove-AzRoleAssignment -full' for more help.


Azure_AppService_DP_Use_CNAME_With_SSL 	 | 	 Custom domain with SSL binding must be configured for App Service 	 | 	 Go to Azure Portal --> your App Service --> Settings --> Custom Domains and follow the steps mentioned to configure a custom domain. Run command 'New-AzWebAppSSLBinding' to enable the SSL binding for your custom domain. Run 'Get-Help New-AzWebAppSSLBinding -full' for more help.


Azure_AppService_AuthN_Use_AAD_for_Client_AuthN 	 | 	 App Service must authenticate users using Azure Active Directory backed credentials 	 | 	 Go to Azure Portal --> your App Service --> Settings --> Authentication/Authorization --> turn on 'App Service Authentication' --> Click on 'Azure Active Directory' under Authentication Providers to configure the AAD authentication. There will be a list of options to choose from under 'Action to take when request is not authenticated'. Please make sure that this value is not set to 'Allow Anonymous requests (no action)'. Note: If you are implementing this control via code, then you can attest to the same and mark this as passed. Note: In case of Functions apps, AAD authentication is required only for 'Http Trigger' functions.


Azure_AppService_Deploy_Dont_Use_Publish_Profiles 	 | 	 Publish profile credentials must not be used for App Service deployment 	 | 	 No predefined role should be present in the App Service and all the custom roles must have all 'publishxml' operations added as the Non Actions, e.g. 'microsoft.web/sites/publishxml/read'. Refer https://docs.microsoft.com/en-us/azure/app-service/faq-deployment#i-am-just-getting-started-with-app-service-web-apps-how-do-i-publish-my-code for exploring ways to securely deploy app service.


Azure_AppService_AuthZ_Trigger_Url_AuthN 	 | 	 Trigger URL for the App Service Web Job must require authentication 	 | 	 Use bearer tokens and AAD-based authentication to in the trigger.


Azure_AppService_DP_Encrypt_In_Transit_Webhook 	 | 	 The webhook used for a Web Job must encrypt sensitive data in transit 	 | 	 Encryption in transit in the context of webhooks can be achieved by using HTTPS URLs.


Azure_AppService_DP_Store_Secrets_in_Key_Vault 	 | 	 All App Service secrets should be stored in Key Vault 	 | 	 Refer https://azure.microsoft.com/en-in/documentation/articles/key-vault-get-started/ for configuring Key Vault and storing secrets.


Azure_AppService_Deploy_Use_Notification_Hub 	 | 	 App Service should use Notification Hub for push notification (instead of directly using Push Notification Service) 	 | 	 Refer https://docs.microsoft.com/en-us/azure/notification-hubs/ for details on configuring Notification Hub for push notifications.


Azure_AppService_Config_Disable_Remote_Debugging 	 | 	 Remote debugging must be turned off for App Service 	 | 	 Go to Azure Portal --> your App Service --> Settings --> Configuration --> General Settings --> Remote Debugging --> Click on 'OFF'.


Azure_AppService_Config_Disable_Web_Sockets 	 | 	 Web Sockets should be disabled for App Service 	 | 	 Run command 'Set-AzWebApp -Name '<WebAppName>' -ResourceGroupName '<RGName>' -WebSocketsEnabled `$false'. Run 'Get-Help Set-AzWebApp -full' for more help. Refer: https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/HTML5_Security_Cheat_Sheet.md#websockets


Azure_AppService_BCDR_Use_AlwaysOn 	 | 	 'Always On' should be configured for App Service 	 | 	 Go to Azure Portal --> your App Service --> Settings --> Configuration --> General Settings --> Always On --> Click on 'ON'.


Azure_AppService_Deploy_Use_Latest_Version 	 | 	 The latest version of .NET framework version should be used for App Service 	 | 	 Run command 'Set-AzWebApp -Name '<WebAppName>' -ResourceGroupName '<RGName>' -NetFrameworkVersion 'v4.7''. Run 'Get-Help Set-AzWebApp -full' for more help.


Azure_AppService_Deploy_Use_ARM_Template 	 | 	 Deployment of App Service should be done using ARM template 	 | 	 Use an ARM Template to ensure fully repeatable and secured configuration of a deployment. Refer https://azure.microsoft.com/en-gb/resources/templates/ to get sample quickstart templates.


Azure_AppService_BCDR_Use_Multiple_Instances 	 | 	 App Service must be deployed on a minimum of two instances to ensure availability 	 | 	 Run command 'Set-AzAppServicePlan -Name '<AppServicePlanName>' -ResourceGroupName '<RGName>' -NumberofWorkers '<NumberofInstances>''. Run 'Get-Help Set-AzAppServicePlan -full' for more help.


Azure_AppService_BCDR_Use_App_Backup 	 | 	 Backup feature must be configured to backup data for App Service 	 | 	 Run command 'Edit-AzWebAppBackupConfiguration -FrequencyInterval '1' -FrequencyUnit 'Day' -RetentionPeriodInDays '<0 or 365>' -StartTime '<TimeLessThanOrEqualToCurrentTime>' -Name '<WebAppName>' -ResourceGroupName '<RGName>' -StorageAccountUrl '<StorageAccountUrl>' -KeepAtLeastOneBackup'. Run 'Get-Help Edit-AzWebAppBackupConfiguration -full' for more help.


Azure_AppService_Audit_Enable_Logging_and_Monitoring 	 | 	 Auditing and Monitoring must be enabled for App Service 	 | 	 Run command 'Set-AzWebApp -Name '<WebAppName>' -ResourceGroupName '<RGName>' -DetailedErrorLoggingEnabled `$true -HttpLoggingEnabled `$true -RequestTracingEnabled `$true'. Run 'Get-Help Set-AzWebApp -full' for more help.


Azure_AppService_BCDR_Configure_Auto_Healing 	 | 	 Auto healing should be configured for App Service 	 | 	 Refer https://azure.microsoft.com/en-in/blog/auto-healing-windows-azure-web-sites/ for details on configuring auto healing.


Azure_AppService_DP_Dont_Allow_HTTP_Access 	 | 	 App Service must only be accessible over HTTPS 	 | 	 Run command 'Set-AzWebApp -Name '<WebAppName>' -ResourceGroupName '<RGName>' -HttpsOnly `$true. Run 'Get-Help Set-AzWebApp -full' for more help.


Azure_AppService_DP_Website_Load_Certificates_Not_All 	 | 	 WEBSITE_LOAD_CERTIFICATES parameter must not be set to '*' (i.e. all) for App Service 	 | 	 Go to Azure Portal --> your App Service --> Settings --> Configuration --> Application Settings --> Check for 'WEBSITE_LOAD_CERTIFICATES' key and make sure that value is not set to '*'. Instead choose the specific certificate that is required by the App Service. Refer https://msftplayground.com/2016/11/using-certificates-azure-app-services/ for more details.


Azure_AppService_DP_Configure_Rotate_Keys_Fn 	 | 	 Keys should be renewed after a regular interval 	 | 	 Refer https://docs.microsoft.com/en-us/azure/azure-functions/functions-bindings-http-webhook#authorization-keys for details on Host keys in Functions app.


Azure_AppService_DP_Dont_Share_HostKeys_Fn 	 | 	 Host key access should not be shared with individual clients 	 | 	 Refer https://docs.microsoft.com/en-us/azure/azure-functions/functions-bindings-http-webhook#authorization-keys for details on Host keys in Functions app.


Azure_AppService_Authz_Use_Function_Authorization_level_Fn 	 | 	 Authorization level for HTTP Trigger function in a function app should be set to 'Function' 	 | 	 Go to Azure Portal --> your Functions App --> your HTTP Trigger Function --> Integrate --> Change Authorization level.


Azure_AppService_Configure_EditMode_ReadOnly_Fn 	 | 	 Functions app edit mode should be set to Read Only 	 | 	 Go to Azure Portal --> your Functions App --> Functions app settings --> Function app edit mode --> Click on 'Read Only'.


Azure_AppService_DP_Use_Individual_FunctionKeys_Fn 	 | 	 Different functions keys must be generated and shared with individual clients. 	 | 	 Go to Azure Portal --> your Functions App --> your Function --> Manage --> Add New Function Key.


Azure_AppService_DP_Restrict_CORS_Access 	 | 	 Ensure that CORS access is granted to a limited set of trusted origins. 	 | 	 Go to Azure Portal --> your App Service --> API --> CORS --> Provide the specific domain names that should be allowed to make cross-origin calls. Note: No action is needed if you are not using CORS for your app.


Azure_AppService_Configure_Important_Alerts 	 | 	 Alerts should be configured to track unauthorized access attempts for the AppService. 	 | 	 Go to Azure Portal --> your App Service --> Monitoring --> Alerts --> Add Alert. Set alert on metrics with name 'Http 403'(unauthorized response) and 'Http 401'(forbidden response).


Azure_AppService_AuthN_Use_Managed_Service_Identity 	 | 	 Use Managed Service Identity (MSI) for accessing other AAD-protected resources from the app service. 	 | 	 Go to Azure Portal --> your App Service --> Settings --> Identity --> System assigned --> ON


Azure_AppService_DP_Dont_Allow_HTTP_Access_Fn 	 | 	 Function App must only be accessible over HTTPS 	 | 	 Run command 'Set-AzResource -ResourceName '<WebAppName>' -ResourceGroupName '<RGName>' -ResourceType 'Microsoft.Web/sites' -Properties @{httpsOnly='true'} -Force '. Run 'Get-Help Set-AzResource -full' for more help. Note:'HttpsOnly' is required only for 'Http Trigger' functions.


Azure_AppService_DP_Use_Secure_TLS_Version 	 | 	 Use approved version of TLS for the App Service 	 | 	 Go to Azure Portal --> your App Service --> Settings --> TLS/SSL --> Minimum TLS version --> set to org approved version (see detailed logs).


Azure_AppService_DP_Verify_Installed_Extensions 	 | 	 Extensions installed on a App Service should be carefully reviewed 	 | 	 Go to Azure Portal --> your App Service --> Development Tools --> Extensions --> Verify installed extensions.


Azure_AppService_AuthZ_Configure_IP_Restrictions 	 | 	 Setup IP-based access restrictions for App Service if feasible 	 | 	 Consider using IP-based access restrictions for App Service if feasible. Steps: Go to Azure Portal --> your App Service --> Networking --> Access Restrictions --> Configure Access Restrictions --> Add/Verify access restriction rule for app and scm site. For more information, refer: https://docs.microsoft.com/en-us/azure/app-service/app-service-ip-restrictions


Azure_AppService_DP_Review_CORS_Request_Credential 	 | 	 Review use of credentials in CORS request for App Service 	 | 	 Go to Azure Portal --> your App Service --> API --> CORS --> Request Credentials --> Review if you need to enable 'Access-Control-Allow-Credentials'. Note: No action is needed if you are not using CORS for your app.


