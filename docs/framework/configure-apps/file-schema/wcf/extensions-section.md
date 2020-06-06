---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855356"
---
# <a name="extensions-section"></a>\<extensions>section
Tento oddíl konfigurace obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
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
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|Tato část obsahuje podřízené prvky, které určují rozšíření chování, které umožňuje uživateli přizpůsobit chování služby nebo koncového bodu.|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|Tato část umožňuje použití vlastního prvku vazby z počítače nebo konfiguračního souboru aplikace.|  
|[\<bindingExtensions>](bindingextensions.md)|Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňuje uživateli přizpůsobit vazby.|  
|[\<endpointExtensions>](endpointextensions.md)|Tato část obsahuje podřízené prvky, které registrují standardní koncové body.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|systém.ServiceModel|Kořenový element všech elementů konfigurace služby WCF.|
