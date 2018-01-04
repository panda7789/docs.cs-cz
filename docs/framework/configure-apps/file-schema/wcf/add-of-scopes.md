---
title: "&lt;add&gt; – &lt;scopes&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 012d86297f75874b57231d7c347c7412ad04aa1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a>&lt;add&gt; – &lt;scopes&gt;
Přidá obor vlastní identifikátor Uri, který můžete použít k filtrování koncové body služby během dotazu.  
  
\<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<endpointDiscovery >  
\<obory >  
\<Přidat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
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
|rozsah|Identifikátor URI, který obsahuje informace o oboru koncového bodu, který lze použít v odpovídající kritériím pro vyhledání služeb.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Obsahuje kolekci elementů konfigurace, které určují obor vlastní identifikátory URI, které mohou být použity k filtrování koncové body služby během dotazu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
