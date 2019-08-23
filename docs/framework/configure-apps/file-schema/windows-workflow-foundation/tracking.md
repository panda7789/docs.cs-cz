---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 79230c65d8eb8c15cef5dce73698448ca7b1e003
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947317"
---
# <a name="tracking"></a><span data-ttu-id="5b5c6-101">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5b5c6-101">\<tracking></span></span>
<span data-ttu-id="5b5c6-102">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="5b5c6-103">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Konfigurace sledování pracovního postupu](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="5b5c6-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="5b5c6-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5b5c6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5b5c6-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5b5c6-105">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b5c6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b5c6-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b5c6-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5b5c6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5b5c6-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b5c6-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b5c6-109">Attributes</span></span>  
 <span data-ttu-id="5b5c6-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="5b5c6-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b5c6-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5b5c6-111">Child Elements</span></span>  
  
|<span data-ttu-id="5b5c6-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b5c6-112">Element</span></span>|<span data-ttu-id="5b5c6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5b5c6-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b5c6-114">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="5b5c6-114">\<participants></span></span>](participants.md)|<span data-ttu-id="5b5c6-115">Kolekce elementů konfigurace definujících účastníky, kteří se přihlásili k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-115">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="5b5c6-116">Sledování účastníci obsahují logiku ke zpracování datové části ze záznamů sledování (například jejich může rozhodnout pro zápis do souboru).</span><span class="sxs-lookup"><span data-stu-id="5b5c6-116">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="5b5c6-117">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5b5c6-117">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="5b5c6-118">Sledování profil filtrování záznamů sledování vyzařováno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-118">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b5c6-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5b5c6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5b5c6-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b5c6-120">Element</span></span>|<span data-ttu-id="5b5c6-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5b5c6-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b5c6-122">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5b5c6-122">system.ServiceModel</span></span>|<span data-ttu-id="5b5c6-123">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b5c6-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b5c6-124">Remarks</span></span>  
 <span data-ttu-id="5b5c6-125">Sledování vám poskytuje možnost prozkoumat provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-125">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="5b5c6-126">Pracovní postup sledování infrastruktury nástroje pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-126">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="5b5c6-127">Například při spuštění instance pracovního postupu, nebo dokončí jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-127">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="5b5c6-128">Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-128">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="5b5c6-129">Můžete například pracovní postup představuje pořadí zpracování systému může být id objednávky extrahována spolu se záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-129">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="5b5c6-130">Obecně platí, že povolení sledování WF usnadňuje diagnostiku nebo obchodní analýzu v průběhu provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b5c6-130">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5c6-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b5c6-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="5b5c6-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5b5c6-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
