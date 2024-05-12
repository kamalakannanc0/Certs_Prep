Azure AI Services provides multiple layers of services.

###### Regenerate Keys:
`az cognitiveservices account keys regenerate`

Each AI service provided with two keys, enabling you to regenerate without the service interruption.
recommended way to use the one key for all production applications. If you want to regenerate swtich the applications to key 2 and regenerate the key 1 and switch again the applications to the key 1.

Regenerate Key  
Azure Portal -> Resource key's and Endpoint Pane

##### Protect keys with Azure Key Vault
Azure Key Vault - you can stores secrets (user & password) 

<img src="https://github.com/kamalakannan143/Certs_Prep/assets/42050635/80672ad0-0b93-4b58-8043-6a125e697f00" width="500" height="500">



##### Token Based Authentication:
When using REST interface, AI services requires token based authentication.
1) **_In this case subscription key is presented in the initial request and it will be valid for 10 mins._**
2) Subsequent requests must present the token to validate that the caller has been authenticated.

**Note: when using SDK the obtain token and the validation to be handled by the SDK itself**

#### Microsoft EntraID Authentication
Entra ID Auth Services supports enabling to grant access to specific service principals or managed identities

##### Diff ways authenticate using Entra ID
##### Authenticate using service principal
**Create a Custom Subdomain** - Azure portal, Azure CLI, powershell

1) Create a subdomain using powershell in Azure CLI
```powershell
Set-AzContext -SubscriptionName <Your-Subscription-Name>
```
2) Create Azure AI service resource by specifying a custom domain
```powershell
$account = New-AzCognitiveServicesAccount -ResourceGroupName <your-resource-group-name> -name <your-account-name> -Type <your-account-type> -SkuName <your-sku-type> -Location <your-region> -CustomSubdomainName <your-unique-subdomain-name>
```
**Assign a Role to Service Principal**
3) As of know we have created a custom subdomain that linked with the azure resource. next we have assign a roles to the service principal.

```powershell
$SecureStringPassword = ConvertTo-SecureString -String <your-password> -AsPlainText -Force

$app = New-AzureADApplication -DisplayName <your-app-display-name> -IdentifierUris <your-app-uris> -PasswordCredentials $SecureStringPassword
```
4) 
