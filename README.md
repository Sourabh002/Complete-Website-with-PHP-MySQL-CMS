1. [Azure_APIManagement_AuthZ_Grant_Min_RBAC_Access](#Azure_APIManagement_AuthZ_Grant_Min_RBAC_Access)

2. [Azure_APIManagement_Audit_Enable_Alerts](#Azure_APIManagement_Audit_Enable_Alerts)

3. [Azure_APIManagement_Audit_Enable_Diagnostics_Log](#Azure_APIManagement_Audit_Enable_Diagnostics_Log)

## Azure_APIManagement_AuthZ_Grant_Min_RBAC_Access
|Control Id|Description|Notes|
|:---------|:----------|:-------------|
|Azure_APIManagement_AuthZ_Grant_Min_RBAC_Access|All users/identities must be granted minimum required permissions using Role Based Access Control (RBAC)||




## Azure_APIManagement_Audit_Enable_Alerts
|Control Id|Description|Notes|
|:---------|:----------|:-------------|
|Azure_APIManagement_Audit_Enable_Alerts|Metric alert rules must be configured for critical actions on API Management service||




## Azure_APIManagement_Audit_Enable_Diagnostics_Log
|Control Id|Description|Notes|
|:---------|:----------|:-------------|
|Azure_APIManagement_Audit_Enable_Diagnostics_Log|Diagnostics logs must be enabled with a retention period of at least $($this.ControlSettings.Diagnostics_RetentionPeriod_Min) days||



