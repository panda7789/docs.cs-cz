---
title: '&lt;bookmarkResumptionQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: f0721e7e14d543b1ff212fe59ed6a2de0a8a9968
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308410"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a>&lt;bookmarkResumptionQuery&gt; služby WCF

Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.  
  
Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
  
\<system.serviceModel>  
\<sledování >  
\<profily >  
\<profil trackingProfile >  
\<pracovní postup >  
\<bookmarkResumptionQueries >  
\<bookmarkResumptionQuery >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
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
|`name`|Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.|  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
