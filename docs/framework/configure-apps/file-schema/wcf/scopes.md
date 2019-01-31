---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: eee6382c578648866045fd9b283454d9e0e76fcb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275021"
---
# <a name="scopes"></a>\<obory >
Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.  
  
\<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<endpointDiscovery>  
\<obory >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|Přidá informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
