---
title: "&lt;activityStateQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de042732e7957fa6ea8c22d03ff6892ee1e912f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequerygt-of-wcf"></a>&lt;activityStateQuery&gt; služby WCF
Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu. Například můžete udržovat přehled o každém dokončení aktivity "Odeslat E-Mail" v rámci instance pracovního postupu. Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity. Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.  
  
 Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
 \<system.serviceModel >  
\<sledování >  
\<trackingProfile >  
\<pracovní postup >  
\<activityStateQueries >  
\<activityStateQuery >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Název aktivity activityName|Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|Kolekce argumenty přidružené k tomuto dotazu aktivity.|  
|[\<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.|  
|[\<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|Kolekce proměnných spojených s Tento dotaz aktivity.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<faultPropagationQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.|  
  
## <a name="remarks"></a>Poznámky  
 Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu. Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění. Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované. Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>    
 <xref:System.Activities.Tracking.ActivityStateQuery>     
 [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
