---
title: <add> z <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926633"
---
# <a name="add-of-scopes"></a>\<Přidat > \<oborů >
Přidá identifikátor URI vlastního rozsahu, který lze použít k filtrování koncových bodů služby během dotazu.  
  
\<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
\<endpointDiscovery>  
\<> oborů  
\<add>  
  
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
  
|Atribut|Popis|  
|---------------|-----------------|  
|rozsah|Identifikátor URI, který obsahuje informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> oborů](scopes.md)|Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
