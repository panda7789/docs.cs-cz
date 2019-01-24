---
title: '&lt;activityScheduledQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 5430058049e8a09c1e2a289e1f997338c23b9d94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492153"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a>&lt;activityScheduledQueries&gt; služby WCF
Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.  
  
Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<sledování >  
\<profiles>  
\<trackingProfile>  
\<pracovní postup >  
\<activityScheduledQueries>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  

Žádné  
  
### <a name="child-elements"></a>Podřízené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|Dotaz, který se používá ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.|  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<workflow>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
