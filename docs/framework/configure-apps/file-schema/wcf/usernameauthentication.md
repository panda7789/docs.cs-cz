---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940535"
---
# <a name="usernameauthentication"></a>\<userNameAuthentication>
Určuje přihlašovací údaje služby na základě uživatelského jména a hesla.  
  
 \<system.ServiceModel>  
\<> chování  
\<serviceBehaviors>  
\<> chování  
\<serviceCredentials>  
\<userNameAuthentication>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|A <xref:System.TimeSpan> určuje maximální dobu, po kterou je token uložen v mezipaměti. Výchozí hodnota je 00:15:00.|  
|`cacheLogonTokens`|Logická hodnota, která určuje, zda jsou přihlašovací tokeny ukládány do mezipaměti. Výchozí hodnota je `false`.|  
|`customUserNamePasswordValidatorType`|Řetězec, který určuje typ vlastního validátoru hesla uživatele, který se má použít. Výchozí hodnota je prázdný řetězec.|  
|`includeWindowsGroups`|Logická hodnota určující, zda jsou skupiny systému Windows zahrnuty v kontextu zabezpečení. Výchozí hodnota je `true`.<br /><br /> Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení. Tuto vlastnost nastavte na `false` , pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.|  
|`maxCacheLogonTokens`|Celé číslo, které určuje maximální počet přihlašovacích tokenů pro ukládání do mezipaměti. Tato hodnota by měla být větší než nula. Výchozí hodnota je 128.|  
|`membershipProviderName`|`username`Pokud je `clientCredentialType` atribut vazby nastaven na hodnotu, uživatelské jméno je namapováno na účty systému Windows. Toto chování můžete přepsat pomocí tohoto atributu, což je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnoty, která poskytuje příslušný mechanismus ověřování hesla.|  
|`userNamePasswordValidationMode`|Určuje způsob, jakým se ověřuje heslo k uživatelskému jménu. Platné hodnoty jsou:<br /><br /> – Windows<br />– MembershipProvider<br />– Vlastní<br /><br /> Výchozí hodnota je Windows. Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud žádná z vazeb používaných službou není nakonfigurovaná pro ověřování pomocí uživatelského jména a hesla, atributy pro tento element se ignorují. Mezi ně `customUserNamePasswordValidatorType`patří `includeWindowsGroups` ,`membershipProviderName`, a `userNamePasswordValidationMode`.  
  
 Pokud není žádná z vazeb používaných službou nakonfigurovaná tak, aby pro uživatelské jméno a heslo používala ověřování systému Windows, ignorují se nastavení související s ukládáním přihlašovacích tokenů do mezipaměti. Mezi ně patří `cacheLogonTokenLifetime`, `cacheLogonTokens`a `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
