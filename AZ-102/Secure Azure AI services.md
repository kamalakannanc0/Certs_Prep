Azure AI Services provides multiple layers of services.

###### Regenerate Keys:
`az cognitiveservices account keys regenerate`

Each AI service provided with two keys, enabling you to regenerate without the service interruption.
recommended way to use the one key for all production applications. If you want to regenerate swtich the applications to key 2 and regenerate the key 1 and switch again the applications to the key 1.

Regenerate Key  
Azure Portal -> Resource key's and Endpoint Pane

##### Protect keys with Azure Key Vault
