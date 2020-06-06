---
title: <windowsAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399116"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<windowsAuthentication> z \<serviceCredentials>
Určuje nastavení pověření služby systému Windows.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`includeWindowsGroups`|Volitelný logický atribut, který určuje, zda systém zahrnuje skupiny systému Windows v kontextu zabezpečení. Výchozí formát je `true`.<br /><br /> Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení. Nastavte tento atribut na, `false` Pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.|  
|`allowAnonymousLogons`|Volitelný logický atribut, který určuje, zda jsou povoleny anonymní neověřené volající. Výchozí formát je `false`.<br /><br /> Pokud `clientCredentialType` je atribut vazby nastaven na `Windows` , systém nepovoluje anonymní volající. To znamená, že přístup k systému má povolen pouze ověřený volající domény nebo pracovní skupiny. Toto chování můžete přepsat pomocí tohoto atributu.<br /><br /> Toto nastavení se používá s mimořádnou opatrností.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek použijte k určení, zda má být povolen anonymní přístup uživatelů systému Windows nastavením `allowAnonymousLogons` atributu. Nastavením atributu můžete také určit, jestli se mají zahrnout informace o skupině, ke kterým uživatelé patří, do AuthorizationContext `includeWindowsGroups` . Pokud je nastavená na `true` (výchozí nastavení), může služba určit skupiny systému Windows, ke kterým klient patří.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
