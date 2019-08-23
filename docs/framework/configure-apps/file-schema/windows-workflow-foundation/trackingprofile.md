---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8b8cfe95a646563642e7425fdb4b5257cafa466f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947304"
---
# <a name="trackingprofile"></a><span data-ttu-id="e8848-101">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e8848-101">\<trackingProfile></span></span>
<span data-ttu-id="e8848-102">Představuje konfigurační oddíl pro vytvoření odběru záznamů sledování pracovních postupů v účastníkovi sledování.</span><span class="sxs-lookup"><span data-stu-id="e8848-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="e8848-103">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="e8848-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e8848-104">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="e8848-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="e8848-105">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v článku [sledování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [profily](../../../windows-workflow-foundation/tracking-profiles.md)trasování a sledování.</span><span class="sxs-lookup"><span data-stu-id="e8848-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e8848-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e8848-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e8848-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e8848-107">\<tracking></span></span>  
<span data-ttu-id="e8848-108">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e8848-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8848-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8848-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8848-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8848-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e8848-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8848-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8848-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8848-112">Attributes</span></span>  
  
|<span data-ttu-id="e8848-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e8848-113">Attribute</span></span>|<span data-ttu-id="e8848-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e8848-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8848-115">name</span><span class="sxs-lookup"><span data-stu-id="e8848-115">name</span></span>|<span data-ttu-id="e8848-116">Řetězec, který určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="e8848-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8848-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e8848-117">Child Elements</span></span>  
  
|<span data-ttu-id="e8848-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8848-118">Element</span></span>|<span data-ttu-id="e8848-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e8848-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8848-120">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="e8848-120">\<participants></span></span>](participants.md)|<span data-ttu-id="e8848-121">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e8848-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8848-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e8848-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e8848-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8848-123">Element</span></span>|<span data-ttu-id="e8848-124">Popis</span><span class="sxs-lookup"><span data-stu-id="e8848-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8848-125">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e8848-125">\<tracking></span></span>](tracking.md)|<span data-ttu-id="e8848-126">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e8848-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8848-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8848-127">Remarks</span></span>  
 <span data-ttu-id="e8848-128">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="e8848-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e8848-129">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e8848-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="e8848-130">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="e8848-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="e8848-131">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="e8848-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="e8848-132">Existuje několik typů dotazů, které umožňují přihlášení k odběru různých tříd <xref:System.Activities.Tracking.TrackingRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="e8848-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="e8848-133">Úplný seznam dotazů najdete v tématu [ \<účastníci >](participants.md) a [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e8848-133">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="e8848-134">Následující příklad ukazuje profil sledování v konfiguračním souboru, který umožňuje sledování účastníka přihlásit k odběru `Started` událostí pracovního postupu a. `Completed`</span><span class="sxs-lookup"><span data-stu-id="e8848-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8848-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8848-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="e8848-136">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e8848-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e8848-137">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="e8848-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
