---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151907"
---
# \<tracking>
<span data-ttu-id="ca897-101">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ca897-101">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="ca897-102">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Konfigurace sledování pracovního postupu](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ca897-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="ca897-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca897-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca897-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ca897-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ca897-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ca897-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca897-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="ca897-106">Attributes</span></span>  
 <span data-ttu-id="ca897-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="ca897-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca897-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ca897-108">Child Elements</span></span>  
  
|<span data-ttu-id="ca897-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca897-109">Element</span></span>|<span data-ttu-id="ca897-110">Description</span><span class="sxs-lookup"><span data-stu-id="ca897-110">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="ca897-111">Kolekce elementů konfigurace definujících účastníky, kteří se přihlásili k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="ca897-111">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="ca897-112">Sledování účastníci obsahují logiku ke zpracování datové části ze záznamů sledování (například jejich může rozhodnout pro zápis do souboru).</span><span class="sxs-lookup"><span data-stu-id="ca897-112">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="ca897-113">Sledování profil filtrování záznamů sledování vyzařováno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ca897-113">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca897-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ca897-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ca897-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca897-115">Element</span></span>|<span data-ttu-id="ca897-116">Description</span><span class="sxs-lookup"><span data-stu-id="ca897-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca897-117">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ca897-117">system.ServiceModel</span></span>|<span data-ttu-id="ca897-118">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ca897-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca897-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca897-119">Remarks</span></span>  
 <span data-ttu-id="ca897-120">Sledování vám poskytuje možnost prozkoumat provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ca897-120">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="ca897-121">Pracovní postup sledování infrastruktury nástroje pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění.</span><span class="sxs-lookup"><span data-stu-id="ca897-121">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="ca897-122">Například při spuštění instance pracovního postupu, nebo dokončí jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="ca897-122">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="ca897-123">Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ca897-123">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="ca897-124">Můžete například pracovní postup představuje pořadí zpracování systému může být id objednávky extrahována spolu se záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="ca897-124">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="ca897-125">Obecně platí, že povolení sledování WF usnadňuje diagnostiku nebo obchodní analýzu v průběhu provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ca897-125">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca897-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca897-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="ca897-127">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ca897-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
