---
title: "Oddíl &lt;extensions&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c8106f004a25f1e4547e9629b881e5bf216490
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltextensionsgt-section"></a>Oddíl &lt;extensions&gt;
Tento konfigurační oddíl obsahuje kolekci rozšíření, která uživateli umožňuje vytvořit uživatelem definované vazby, chování a dalších aspektů rozšíření.  
  
\<systém. ServiceModel >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Tato část obsahuje podřízené elementy, které určují chování rozšíření, která uživateli umožňuje přizpůsobit chování služba nebo koncový bod.|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|Tato část umožňuje použití vlastní vazby element z počítače nebo konfiguračního souboru aplikace.|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Tato část obsahuje podřízené elementy, které určují vazby rozšíření, které umožňují uživateli upravit vazby.|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Tato část obsahuje podřízené prvky, které zaregistruje standardní koncové body.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|systém.ServiceModel|Kořenový element všechny konfigurační prvky WCF.|
