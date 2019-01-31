---
title: <cancelRequestedQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: bd6157e63761efa954744ab08ea6c66535def514
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281330"
---
# <a name="cancelrequestedquery-of-wcf"></a>\<cancelRequestedQuery > služby WCF

Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.  
  
Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).
  
\<system.serviceModel>  
\<sledování >  
\<profiles>  
\<trackingProfile>  
\<pracovní postup >  
\<cancelRequestedQueries>  
\<cancelRequestedQuery>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`activityName`|Řetězec, který určuje název aktivity, která žádá o zrušení.|  
|`childActivityName`|Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.|  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné
  
### <a name="parent-elements"></a>Nadřazené prvky
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
