# Update Active Directory information with CSV

```
#csv dosya yapısı
#user,telephoneNumber,Title,department

Import-Module ActiveDirectory
$Attribcsv=Import-csv “C:\PS\orh_ad.csv”
ForEach ($user in $Attribcsv)  
{
if($user.telephoneNumber -eq "") {} else {Get-ADUser -Identity $user.user | Set-ADUser -Replace @{telephoneNumber=$user.telephoneNumber}}
if($user.Title -eq "") {} else {Get-ADUser -Identity $user.user | Set-ADUser -Replace @{Title=$user.Title}}
if($user.department -eq "") {} else {Get-ADUser -Identity $user.user | Set-ADUser -Replace @{department=$user.department}}
}
```
