---
title: '&lt;add&gt; – &lt;scopes&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: 961fb3e388e3ae756bd7511ea6c65df6dd2a1486
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705570"
---
# <a name="ltaddgt-of-ltscopesgt"></a>&lt;add&gt; – &lt;scopes&gt;
Přidá vlastní rozsahy identifikátoru Uri, který můžete použít k filtrování koncových bodů služby během dotazu.  
  
\<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<endpointDiscovery>  
\<obory >  
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
|rozsah|Identifikátor URI, který obsahuje informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
