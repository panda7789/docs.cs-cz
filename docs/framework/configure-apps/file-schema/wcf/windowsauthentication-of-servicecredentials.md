---
title: <windowsAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ffddbae7effabcdafdc2638d588bbbf3e42d2c2a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200386"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<windowsAuthentication> of \<serviceCredentials>
Určuje nastavení přihlašovacích údajů služby Windows.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
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
|`includeWindowsGroups`|Volitelný logický atribut, který určuje, zda tento systém zahrnuje skupiny Windows v kontextu zabezpečení. Výchozí hodnota je `true`.<br /><br /> Nastavení tohoto atributu na `true` má dopad na výkon, protože výsledkem rozšíření skupiny úplné. Tento atribut nastavte na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří.|  
|`allowAnonymousLogons`|Volitelný logický atribut, který určuje, jestli jsou povolené anonymní, neověření volající. Výchozí hodnota je `false`.<br /><br /> Když `clientCredentialType` atribut vazby je nastaven na `Windows`, systém nepovoluje anonymní volající. To znamená, že pouze domény nebo pracovní skupině authenticated volající je povolen přístup k systému. Toto chování můžete přepsat pomocí tohoto atributu.<br /><br /> Pomocí tohoto nastavení s nejvyšší opatrností.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element slouží k určení, jestli se má povolit přístup anonymní uživatelé Windows tak, že nastavíte `allowAnonymousLogons` atribut. Můžete také určit, zda mají být zahrnuty informace o skupinách, ke kterému uživatelé patří AuthorizationContext tak, že nastavíte `includeWindowsGroups` atribut. Pokud je nastavena na `true` (výchozí nastavení), službu můžete určit skupiny Windows, na které klient patří.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
