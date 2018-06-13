---
title: '&lt;Sledování&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 38c765c52a7578ed9972cd6fdd8e01440a4d9594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756680"
---
# <a name="lttrackinggt"></a><span data-ttu-id="2c3fd-102">&lt;Sledování&gt;</span><span class="sxs-lookup"><span data-stu-id="2c3fd-102">&lt;tracking&gt;</span></span>
<span data-ttu-id="2c3fd-103">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="2c3fd-104">Další informace v pracovním postupu sledování a jeho konfigurace najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [konfigurace sledování pro pracovní postup](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="2c3fd-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="2c3fd-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c3fd-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2c3fd-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="2c3fd-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c3fd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c3fd-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c3fd-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c3fd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2c3fd-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c3fd-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c3fd-110">Attributes</span></span>  
 <span data-ttu-id="2c3fd-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="2c3fd-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c3fd-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c3fd-112">Child Elements</span></span>  
  
|<span data-ttu-id="2c3fd-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c3fd-113">Element</span></span>|<span data-ttu-id="2c3fd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2c3fd-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c3fd-115">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="2c3fd-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="2c3fd-116">Kolekci elementů konfigurace definování účastníci, přihlásit k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="2c3fd-117">Sledování účastníci obsahují logiku ke zpracování datové části ze záznamů sledování (například jejich může rozhodnout pro zápis do souboru).</span><span class="sxs-lookup"><span data-stu-id="2c3fd-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="2c3fd-118">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2c3fd-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="2c3fd-119">Sledování profil filtrování záznamů sledování vyzařováno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c3fd-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c3fd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2c3fd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c3fd-121">Element</span></span>|<span data-ttu-id="2c3fd-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2c3fd-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c3fd-123">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2c3fd-123">system.ServiceModel</span></span>|<span data-ttu-id="2c3fd-124">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c3fd-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c3fd-125">Remarks</span></span>  
 <span data-ttu-id="2c3fd-126">Sledování vám poskytuje možnost prozkoumat provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="2c3fd-127">Pracovní postup sledování infrastruktury nástroje pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="2c3fd-128">Například při spuštění instance pracovního postupu, nebo dokončí jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="2c3fd-129">Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="2c3fd-130">Můžete například pracovní postup představuje pořadí zpracování systému může být id objednávky extrahována spolu se záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="2c3fd-131">Obecně platí povolení WF sledování usnadňuje diagnostiku nebo obchodní analýza nad spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2c3fd-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3fd-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c3fd-132">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [<span data-ttu-id="2c3fd-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2c3fd-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
