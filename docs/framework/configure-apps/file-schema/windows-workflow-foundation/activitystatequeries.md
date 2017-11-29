---
title: '&lt;activityStateQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9bcf80d215f9b889c59ab6e68d07ca656ffe93b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivitystatequeriesgt"></a>&lt;activityStateQueries&gt;
Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu. Například můžete udržovat přehled o každém dokončení aktivity "Odeslat E-Mail" v rámci instance pracovního postupu. Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity. Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.  
  
 Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
\<system.serviceModel >  
\<sledování >  
\<trackingProfile >  
\<pracovní postup >  
\<activityStateQueries >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|Dotaz, který se používá ke sledování ošetření chyb, které se vyskytují v aktivitě.  K této události dochází pokaždé, když FaultHandler zpracovává chybu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<pracovní postup >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [Pracovní postup sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
