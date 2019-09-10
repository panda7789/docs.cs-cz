---
title: <activityScheduledQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850475"
---
# <a name="activityscheduledquery-of-wcf"></a>\<activityScheduledQuery > WCF

Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.  
  
Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**  
  
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
  
|Atribut|Popis|  
|---------------|-----------------|  
|`activityName`|Řetězec, který určuje název aktivity, která žádá o zrušení.|  
|`childActivityName`|Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.|  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|Kolekce dotazů, které se používají ke sledování aktivity naplánované pro provádění nadřazenou aktivitou.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [Sledování a trasování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)
