---
title: <tracking>služby WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e8f74d635299a965b754536234e6be28e4e7a104
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399421"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="13ab9-102">\<sledování > WCF</span><span class="sxs-lookup"><span data-stu-id="13ab9-102">\<tracking> of WCF</span></span>
<span data-ttu-id="13ab9-103">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="13ab9-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="13ab9-104">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Konfigurace sledování pracovního postupu](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="13ab9-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="13ab9-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="13ab9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13ab9-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="13ab9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="13ab9-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<sledování >**</span><span class="sxs-lookup"><span data-stu-id="13ab9-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13ab9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13ab9-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13ab9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="13ab9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="13ab9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="13ab9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13ab9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="13ab9-111">Attributes</span></span>  
 <span data-ttu-id="13ab9-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="13ab9-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13ab9-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13ab9-113">Child Elements</span></span>  
  
|<span data-ttu-id="13ab9-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="13ab9-114">Element</span></span>|<span data-ttu-id="13ab9-115">Popis</span><span class="sxs-lookup"><span data-stu-id="13ab9-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13ab9-116">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="13ab9-116">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="13ab9-117">Kolekce elementů konfigurace definujících účastníky, kteří se přihlásili k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="13ab9-117">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="13ab9-118">Sledování účastníci obsahují logiku ke zpracování datové části ze záznamů sledování (například jejich může rozhodnout pro zápis do souboru).</span><span class="sxs-lookup"><span data-stu-id="13ab9-118">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="13ab9-119">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="13ab9-119">\<trackingProfile></span></span>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="13ab9-120">Sledování profil filtrování záznamů sledování vyzařováno instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="13ab9-120">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13ab9-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="13ab9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="13ab9-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="13ab9-122">Element</span></span>|<span data-ttu-id="13ab9-123">Popis</span><span class="sxs-lookup"><span data-stu-id="13ab9-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13ab9-124">systém.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="13ab9-124">system.ServiceModel</span></span>|<span data-ttu-id="13ab9-125">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="13ab9-125">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13ab9-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13ab9-126">Remarks</span></span>  
 <span data-ttu-id="13ab9-127">Sledování vám poskytuje možnost prozkoumat provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="13ab9-127">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="13ab9-128">Pracovní postup sledování infrastruktury nástroje pracovního postupu pro vydávání záznamy, které odráží klíče události během provádění.</span><span class="sxs-lookup"><span data-stu-id="13ab9-128">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="13ab9-129">Například při spuštění instance pracovního postupu, nebo dokončí jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="13ab9-129">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="13ab9-130">Sledování lze rovněž extrahovat obchodní relevantní data přidružená k proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="13ab9-130">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="13ab9-131">Můžete například pracovní postup představuje pořadí zpracování systému může být id objednávky extrahována spolu se záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="13ab9-131">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="13ab9-132">Obecně platí, že povolení sledování WF usnadňuje diagnostiku nebo obchodní analýzu v průběhu provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="13ab9-132">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ab9-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13ab9-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="13ab9-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="13ab9-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
