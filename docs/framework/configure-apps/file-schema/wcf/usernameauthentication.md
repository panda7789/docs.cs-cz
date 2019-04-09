---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 5a4cf8d429198b889f2bb362294ba3841c814b26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083137"
---
# <a name="usernameauthentication"></a>\<userNameAuthentication>
Určuje pověření služby na základě uživatelského jména a hesla.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
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
|`cacheLogonTokenLifetime`|A <xref:System.TimeSpan> , která určuje maximální délku doby token se uloží do mezipaměti. Výchozí hodnota je 00:15:00.|  
|`cacheLogonTokens`|Logická hodnota určující, zda jsou uložené v mezipaměti tokeny přihlášení. Výchozí hodnota je `false`.|  
|`customUserNamePasswordValidatorType`|Řetězec, který určuje typ validátoru vlastního uživatelského jména hesla pro použití. Výchozí hodnota je prázdný řetězec.|  
|`includeWindowsGroups`|Logická hodnota určující, zda jsou skupiny Windows zahrnuty v kontextu zabezpečení. Výchozí hodnota je `true`.<br /><br /> Nastavení tohoto atributu na `true` má dopad na výkon, protože výsledkem rozšíření skupiny úplné. Tuto vlastnost nastavte na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří.|  
|`maxCacheLogonTokens`|Celé číslo určující maximální počet tokeny přihlášení do mezipaměti. Tato hodnota by měla být větší než nula. Výchozí hodnota je 128.|  
|`membershipProviderName`|Když `clientCredentialType` atribut vazby je nastaven na `username`, uživatelské jméno je mapováno na účty Windows. Můžete přepsat toto chování pomocí tohoto atributu, což je řetězec, který obsahuje název <xref:System.Web.Security.MembershipProvider> hodnotu, která poskytuje mechanismus ověřování příslušné heslo.|  
|`userNamePasswordValidationMode`|Určuje způsob, v jaké uživatelské jméno je ověřit heslo. Platné hodnoty jsou:<br /><br /> – Windows<br />-MembershipProvider<br />– Vlastní<br /><br /> Výchozí hodnota je Windows. Tento atribut je typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje přihlašovací údaje, který se má použít při ověřování služby, a nastavení příslušného ověřování přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud žádná z vazby používané službou je nakonfigurován pro ověřování založené na jméno/heslo uživatele, atributy u tohoto elementu se ignorují. Patří mezi ně `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, a `userNamePasswordValidationMode`.  
  
 Pokud žádná z vazby používané službou je nakonfigurován pro použití ověřování Windows pro uživatelské jméno/heslo, jsou ignorovány nastavení týkající se ukládání do mezipaměti tokeny přihlášení. Patří mezi ně `cacheLogonTokenLifetime`, `cacheLogonTokens`, a `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
