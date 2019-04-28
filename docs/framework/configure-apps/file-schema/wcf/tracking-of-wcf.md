---
title: <tracking> služby WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: 4aac9f28de746e2a75a079cbaf774f01f4a08fca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758142"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="03ec4-102">\<Tracking > služby WCF</span><span class="sxs-lookup"><span data-stu-id="03ec4-102">\<tracking> of WCF</span></span>
<span data-ttu-id="03ec4-103">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="03ec4-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="03ec4-104">Další informace v sledování pracovních postupů a jeho konfiguraci najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [konfigurace sledování pracovního postupu](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="03ec4-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="03ec4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="03ec4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="03ec4-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="03ec4-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ec4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03ec4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03ec4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03ec4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="03ec4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03ec4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03ec4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="03ec4-110">Attributes</span></span>  
 <span data-ttu-id="03ec4-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="03ec4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03ec4-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03ec4-112">Child Elements</span></span>  
  
|<span data-ttu-id="03ec4-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="03ec4-113">Element</span></span>|<span data-ttu-id="03ec4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="03ec4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03ec4-115">\<participants></span><span class="sxs-lookup"><span data-stu-id="03ec4-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="03ec4-116">Kolekce elementů konfigurace definování účastníci, přihlásit k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="03ec4-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="03ec4-117">Sledování účastníci obsahují logiku ke zpracování datové části ze záznamů sledování (například jejich může rozhodnout pro zápis do souboru).</span><span class="sxs-lookup"><span data-stu-id="03ec4-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="03ec4-118">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="03ec4-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="03ec4-119">Sledování profil filtrování záznamů sledování vyzařováno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="03ec4-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03ec4-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03ec4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="03ec4-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="03ec4-121">Element</span></span>|<span data-ttu-id="03ec4-122">Popis</span><span class="sxs-lookup"><span data-stu-id="03ec4-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03ec4-123">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="03ec4-123">system.ServiceModel</span></span>|<span data-ttu-id="03ec4-124">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="03ec4-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03ec4-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03ec4-125">Remarks</span></span>  
 <span data-ttu-id="03ec4-126">Sledování vám poskytuje možnost prozkoumat provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="03ec4-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="03ec4-127">Pracovní postup sledování infrastruktury nástroje pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění.</span><span class="sxs-lookup"><span data-stu-id="03ec4-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="03ec4-128">Například při spuštění instance pracovního postupu, nebo dokončí jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="03ec4-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="03ec4-129">Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="03ec4-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="03ec4-130">Můžete například pracovní postup představuje pořadí zpracování systému může být id objednávky extrahována spolu se záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="03ec4-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="03ec4-131">Obecně platí povolení WF sledování zajišťuje diagnostiky nebo obchodní analýza prostřednictvím pracovního postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="03ec4-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ec4-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03ec4-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="03ec4-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="03ec4-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
