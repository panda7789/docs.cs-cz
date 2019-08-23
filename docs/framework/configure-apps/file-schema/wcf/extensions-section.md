---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 4c8b5fe6eef1863ee3f02cb761a3aac61406e446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918973"
---
# <a name="extensions-section"></a>\<oddíl rozšíření >
Tento oddíl konfigurace obsahuje kolekci rozšíření, která umožňují uživateli vytvořit uživatelsky definované vazby, chování a další aspekty rozšíření.  
  
\<system.ServiceModel>  
  
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
|[\<behaviorExtensions>](behaviorextensions.md)|Tato část obsahuje podřízené prvky, které určují rozšíření chování, které umožňuje uživateli přizpůsobit chování služby nebo koncového bodu.|  
|[\<bindingElementExtensions >](bindingelementextensions.md)|Tato část umožňuje použití vlastního prvku vazby z počítače nebo konfiguračního souboru aplikace.|  
|[\<bindingExtensions >](bindingextensions.md)|Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňuje uživateli přizpůsobit vazby.|  
|[\<endpointExtensions>](endpointextensions.md)|Tato část obsahuje podřízené prvky, které registrují standardní koncové body.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|systém.ServiceModel|Kořenový element všech elementů konfigurace služby WCF.|
