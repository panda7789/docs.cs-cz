---
title: <extensions> Oddíl
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268285"
---
# <a name="extensions-section"></a>\<Rozšíření > části
Tento oddíl konfigurace obsahuje kolekci rozšíření, které umožňují uživateli vytvořit uživatelem definované vazby, chování a další aspekty rozšíření.  
  
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
|[\<behaviorExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Tato část obsahuje podřízené prvky, které určují chování rozšíření, které umožňují uživatelům přizpůsobit chování služby nebo koncového bodu.|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|Tato část umožňuje používat vlastní prvek vazby z počítače nebo konfiguračního souboru aplikace.|  
|[\<bindingExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Tato část obsahuje podřízené prvky, které určují rozšíření vazby, které umožňují uživateli upravit vazby.|  
|[\<endpointExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Tato část obsahuje podřízené prvky, které se zaregistruje standardních koncových bodů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|systém.ServiceModel|Kořenový element všechny elementy konfigurace WCF.|
