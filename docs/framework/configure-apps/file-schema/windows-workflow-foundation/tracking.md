---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151907"
---
# <a name="tracking"></a><span data-ttu-id="e9a01-101">\<sledování></span><span class="sxs-lookup"><span data-stu-id="e9a01-101">\<tracking></span></span>
<span data-ttu-id="e9a01-102">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e9a01-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="e9a01-103">Další informace o sledování pracovního postupu a jeho konfiguraci naleznete v [tématu Sledování a trasování pracovního postupu](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Konfigurace sledování pracovního postupu](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e9a01-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="e9a01-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9a01-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9a01-105">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e9a01-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e9a01-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sledování>**</span><span class="sxs-lookup"><span data-stu-id="e9a01-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a01-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9a01-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9a01-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9a01-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e9a01-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9a01-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9a01-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9a01-110">Attributes</span></span>  
 <span data-ttu-id="e9a01-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="e9a01-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9a01-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e9a01-112">Child Elements</span></span>  
  
|<span data-ttu-id="e9a01-113">Element</span><span class="sxs-lookup"><span data-stu-id="e9a01-113">Element</span></span>|<span data-ttu-id="e9a01-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e9a01-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9a01-115">\<účastníci></span><span class="sxs-lookup"><span data-stu-id="e9a01-115">\<participants></span></span>](participants.md)|<span data-ttu-id="e9a01-116">Kolekce konfiguračních prvků definujících účastníky, kteří se přihlásí ke sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="e9a01-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="e9a01-117">Sledování účastníci obsahují logiku ke zpracování datové části ze záznamů sledování (například jejich může rozhodnout pro zápis do souboru).</span><span class="sxs-lookup"><span data-stu-id="e9a01-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="e9a01-118">\<trackingProfil></span><span class="sxs-lookup"><span data-stu-id="e9a01-118">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="e9a01-119">Sledování profil filtrování záznamů sledování vyzařováno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e9a01-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9a01-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e9a01-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e9a01-121">Element</span><span class="sxs-lookup"><span data-stu-id="e9a01-121">Element</span></span>|<span data-ttu-id="e9a01-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e9a01-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9a01-123">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e9a01-123">system.ServiceModel</span></span>|<span data-ttu-id="e9a01-124">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e9a01-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9a01-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9a01-125">Remarks</span></span>  
 <span data-ttu-id="e9a01-126">Sledování vám poskytuje možnost prozkoumat provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e9a01-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="e9a01-127">Pracovní postup sledování infrastruktury nástroje pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění.</span><span class="sxs-lookup"><span data-stu-id="e9a01-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="e9a01-128">Například při spuštění instance pracovního postupu, nebo dokončí jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="e9a01-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="e9a01-129">Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e9a01-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="e9a01-130">Můžete například pracovní postup představuje pořadí zpracování systému může být id objednávky extrahována spolu se záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="e9a01-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="e9a01-131">Povolení sledování služby WF obecně usnadňuje diagnostiku nebo obchodní analýzu při provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e9a01-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a01-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9a01-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="e9a01-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e9a01-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
