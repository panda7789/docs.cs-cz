---
title: <trackingProfile>služby WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: c5df03d63653e658a23a36e8943c06f156d2ae00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854937"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="8265f-102">\<trackingProfile>služby WCF</span><span class="sxs-lookup"><span data-stu-id="8265f-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="8265f-103">Představuje konfigurační oddíl pro vytvoření odběru záznamů sledování pracovních postupů v účastníkovi sledování.</span><span class="sxs-lookup"><span data-stu-id="8265f-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="8265f-104">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="8265f-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="8265f-105">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="8265f-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="8265f-106">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v článku [sledování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [profily](../../../windows-workflow-foundation/tracking-profiles.md)trasování a sledování.</span><span class="sxs-lookup"><span data-stu-id="8265f-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="8265f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8265f-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8265f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8265f-108">Attributes and Elements</span></span>  

<span data-ttu-id="8265f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8265f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8265f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8265f-110">Attributes</span></span>  
  
|<span data-ttu-id="8265f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8265f-111">Attribute</span></span>|<span data-ttu-id="8265f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8265f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8265f-113">name</span><span class="sxs-lookup"><span data-stu-id="8265f-113">name</span></span>|<span data-ttu-id="8265f-114">Řetězec, který určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="8265f-114">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8265f-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8265f-115">Child Elements</span></span>  
  
|<span data-ttu-id="8265f-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="8265f-116">Element</span></span>|<span data-ttu-id="8265f-117">Description</span><span class="sxs-lookup"><span data-stu-id="8265f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="8265f-118">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8265f-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8265f-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8265f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8265f-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="8265f-120">Element</span></span>|<span data-ttu-id="8265f-121">Description</span><span class="sxs-lookup"><span data-stu-id="8265f-121">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="8265f-122">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8265f-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8265f-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8265f-123">Remarks</span></span>  
 <span data-ttu-id="8265f-124">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="8265f-124">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="8265f-125">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8265f-125">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="8265f-126">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="8265f-126">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="8265f-127">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="8265f-127">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="8265f-128">Existuje několik typů dotazů, které umožňují přihlášení k odběru různých tříd <xref:System.Activities.Tracking.TrackingRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="8265f-128">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="8265f-129">Úplný seznam dotazů naleznete v tématu [\<participants>](../windows-workflow-foundation/participants.md) a [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8265f-129">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="8265f-130">Následující příklad ukazuje profil sledování v konfiguračním souboru, který umožňuje sledování účastníka přihlásit k odběru `Started` `Completed` událostí pracovního postupu a.</span><span class="sxs-lookup"><span data-stu-id="8265f-130">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="8265f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8265f-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="8265f-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8265f-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8265f-133">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8265f-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
