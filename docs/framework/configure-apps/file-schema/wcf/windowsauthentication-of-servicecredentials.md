---
title: <windowsAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 81793b0d58a95166bc23f98d46ce94a5f1e1d018
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940294"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<windowsAuthentication > \<ServiceCredentials >
Určuje nastavení pověření služby systému Windows.  
  
 \<system.ServiceModel>  
\<> chování  
\<serviceBehaviors>  
\<> chování  
\<serviceCredentials>  
\<windowsAuthentication>  
  
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
|`includeWindowsGroups`|Volitelný logický atribut, který určuje, zda systém zahrnuje skupiny systému Windows v kontextu zabezpečení. Výchozí hodnota je `true`.<br /><br /> Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření úplného seskupení. Nastavte tento atribut na `false` , pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.|  
|`allowAnonymousLogons`|Volitelný logický atribut, který určuje, zda jsou povoleny anonymní neověřené volající. Výchozí hodnota je `false`.<br /><br /> `Windows`Pokud je `clientCredentialType` atribut vazby nastaven na, systém nepovoluje anonymní volající. To znamená, že přístup k systému má povolen pouze ověřený volající domény nebo pracovní skupiny. Toto chování můžete přepsat pomocí tohoto atributu.<br /><br /> Toto nastavení se používá s mimořádnou opatrností.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek použijte k určení, zda má být povolen anonymní přístup uživatelů systému Windows `allowAnonymousLogons` nastavením atributu. Nastavením `includeWindowsGroups` atributu můžete také určit, jestli se mají zahrnout informace o skupině, ke kterým uživatelé patří, do AuthorizationContext. Pokud je nastavená na `true` (výchozí nastavení), může služba určit skupiny systému Windows, ke kterým klient patří.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
