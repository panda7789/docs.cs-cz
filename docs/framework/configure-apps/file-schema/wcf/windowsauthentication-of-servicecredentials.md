---
title: "&lt;windowsAuthentication&gt; – &lt;serviceCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dbc4c3413213aa36468fde6e84671de0e0a31c2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a>&lt;windowsAuthentication&gt; – &lt;serviceCredentials&gt;
Určuje nastavení pověření služby systému Windows.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<windowsAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`includeWindowsGroups`|Volitelný logický atribut, který určuje, zda systém zahrnuje skupiny systému Windows v kontextu zabezpečení. Výchozí hodnota je `true`.<br /><br /> Nastavení tohoto atributu na `true` má dopad na výkon, jako je výsledkem rozšíření skupiny úplné. Nastavte tento atribut `false` Pokud není potřeba vytvořit seznam skupin uživatel patří do.|  
|`allowAnonymousLogons`|Volitelný logický atribut, který určuje, zda jsou povoleny anonymní, neověřené volající. Výchozí hodnota je `false`.<br /><br /> Když `clientCredentialType` atribut vazby je nastaven na `Windows`, systém nepovoluje anonymní volající. To znamená, že pouze doméně nebo pracovní skupině authenticated volající mají povolena přístup k systému. Toto chování můžete přepsat pomocí tohoto atributu.<br /><br /> Pomocí tohoto nastavení s velmi opatrní.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<– serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek slouží k určení, zda povolit přístup anonymní uživatelé Windows nastavením `allowAnonymousLogons` atribut. Můžete také určit, zda mají být zahrnuty informace o skupině, do které patří uživatelé kontext ověřování nastavením `includeWindowsGroups` atribut. Pokud je nastaven na hodnotu `true` (výchozí nastavení), může služba zjistit skupiny systému Windows, na které klient patří.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
