---
title: "&lt;trackingProfile&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23b419842376383c87fee90263bbd0d6468799c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttrackingprofilegt-of-wcf"></a>&lt;trackingProfile&gt; služby WCF
Představuje konfigurační oddíl pro vytváření odběru sledování záznamů v sledování účastník pracovního postupu. Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu. Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.  
  
 Další informace v pracovním postupu sledování a jeho konfigurace najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
 \<system.serviceModel >  
\<sledování >  
\<trackingProfile >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
   <system.serviceModel>  <tracking>      <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>    
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Řetězec, který určuje název profilu sledování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Účastníci >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` vlastnost.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<sledování >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.|  
  
## <a name="remarks"></a>Poznámky  
 Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu. V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu. Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.  
  
 Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování. Existuje několik typy dotazů, které umožňují, že se přihlásíte k různých tříd objektů TrackingRecord HYPERLINK "http://msdn.microsoft.com/en-us/library/system.activities.tracking.trackingrecord (VS.100).aspx". Úplný seznam dotazů najdete v tématu [ \<účastníky >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) a [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...  
  
 Následující příklad ukazuje profil sledování v konfiguračním souboru, který umožňuje účastníkem sledování pro přihlášení k odběru `Started` a `Completed` události pracovního postupu.  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
