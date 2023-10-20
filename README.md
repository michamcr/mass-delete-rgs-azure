# Use PowerShell to Mass Delete Resource Groups

Do not do this in production systems, you can use this for clearing up old test resource groups. 

1. Open Azure Portal https://portal.azure.com
2. Click on Resource Groups
3. Select the Resource Groups that you want to delete
4. Click “Assign tags”
5. Assign name "deleteme"
6. Open PowerShell

## In PowerShell 

1. ```az login```<br>
2. ```az account set -s "yoursubid"```<br>
3. ```az group list --tag deleteme --query [].name -o tsv | ForEach-Object {az group delete --no-wait -n $_}```
5. The script will start executing after you have confirmed `"y"` for every group
6. You can amend point 3 above if you want to bypass individual `"y"` to delete step
