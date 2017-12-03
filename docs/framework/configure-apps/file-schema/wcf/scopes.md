---
title: '&lt;obory&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f198811483edb8a7be882588c38b1f3942f8bb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltscopesgt"></a>&lt;obory&gt;
Obsahuje kolekci elementů konfigurace, které určují obor vlastní identifikátory URI, které mohou být použity k filtrování koncové body služby během dotazu.  
  
\<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<endpointDiscovery >  
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
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|Přidá informace o oboru pro koncový bod, který lze použít v odpovídající kritériím pro vyhledání služeb.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Určuje různé zjišťování nastavení pro koncový bod, například jeho možnosti rozpoznání, obory a vlastní rozšíření jeho metadata.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
