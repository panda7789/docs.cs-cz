---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151855"
---
# <a name="workflow"></a>\<> pracovního postupu
Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> vlastnost.  
  
 Další informace o sledování pracovního postupu a jeho konfiguraci naleznete v [tématu Sledování pracovního postupu a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfil>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>pracovního postupu**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
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
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
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
  
|Atribut|Popis|  
|---------------|-----------------|  
|activityDefinitionId|Řetězec, který určuje ID definice aktivity pracovního postupu sledován.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries.md)|Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.|  
|[\<activityStateQueries>](activitystatequeries.md)|Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu. Můžete například sledovat pokaždé, když se aktivita "Odeslat e-mail" dokončí v rámci instance pracovního postupu. Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity. Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.|  
|[\<záložkaDotazy>](bookmarkresumptionqueries.md)|Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.|  
|[\<cancelRequestedQueries>](cancelrequestedqueries.md)|Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.|  
|[\<customTrackingQueries>](customtrackingqueries.md)|Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.|  
|[\<chybyPropagationQueries>](faultpropagationqueries.md)|Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.  K této události dochází pokaždé, když FaultHandler zpracuje chybu. Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity. Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<trackingProfil>](trackingprofile.md)|Představuje konfigurační oddíl pro vytvoření předplatného záznamů sledování pracovního postupu v účastníkovi sledování. Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu. Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.|  
  
## <a name="remarks"></a>Poznámky  
 Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance určitý pracovní postup za běhu. Instance pracovního postupu sledované je identifikován tento element konfigurace.  
  
 V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu. Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.  
  
 Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování. Existuje několik typů dotazů, které umožňují přihlásit se k odběru různých tříd sledování záznamů. Úplný seznam dotazů naleznete v seznamu podřízených prvků tohoto tématu a [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).  
  
 Následující příklad ukazuje profil sledování v konfiguračním souboru, který umožňuje účastníkovi sledování přihlásit k odběru událostí `Started` a `Completed` pracovního postupu.  
  
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

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [Sledování a trasování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md)
