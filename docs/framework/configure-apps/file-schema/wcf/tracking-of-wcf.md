---
title: '&lt;tracking&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: 7162d66917660a8730f851811643723cd398147c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146729"
---
# <a name="lttrackinggt-of-wcf"></a>&lt;tracking&gt; služby WCF
Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.  
  
 Další informace v sledování pracovních postupů a jeho konfiguraci najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [konfigurace sledování pracovního postupu](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 \<system.serviceModel>  
\<sledování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<participants >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Kolekce elementů konfigurace definování účastníci, přihlásit k odběru sledování záznamů. Sledování účastníci obsahují logiku ke zpracování datové části ze záznamů sledování (například jejich může rozhodnout pro zápis do souboru).|  
|[\<profil trackingProfile >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|Sledování profil filtrování záznamů sledování vyzařováno instance pracovního postupu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|systém.ServiceModel|Kořenový element všechny elementy konfigurace pracovního postupu.|  
  
## <a name="remarks"></a>Poznámky  
 Sledování vám poskytuje možnost prozkoumat provádění pracovního postupu. Pracovní postup sledování infrastruktury nástroje pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění. Například při spuštění instance pracovního postupu, nebo dokončí jsou vydávány sledování záznamů. Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu. Můžete například pracovní postup představuje pořadí zpracování systému může být id objednávky extrahována spolu se záznamem sledování. Obecně platí povolení WF sledování zajišťuje diagnostiky nebo obchodní analýza prostřednictvím pracovního postupu provádění.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [Sledování a trasování pracovních postupů](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
