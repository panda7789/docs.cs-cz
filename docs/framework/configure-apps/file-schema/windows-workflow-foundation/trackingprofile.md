---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 747660df58604dd9384abefccb51ea665f97e2e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139669"
---
# <a name="trackingprofile"></a><span data-ttu-id="0735f-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0735f-101">\<trackingProfile></span></span>
<span data-ttu-id="0735f-102">Představuje konfigurační oddíl pro vytváření odběru sledování záznamů v sledování účastník pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0735f-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="0735f-103">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="0735f-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="0735f-104">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="0735f-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="0735f-105">Další informace v sledování pracovních postupů a jeho konfiguraci najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0735f-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="0735f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0735f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0735f-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="0735f-107">\<tracking></span></span>  
<span data-ttu-id="0735f-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="0735f-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0735f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0735f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0735f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0735f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0735f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0735f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0735f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0735f-112">Attributes</span></span>  
  
|<span data-ttu-id="0735f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0735f-113">Attribute</span></span>|<span data-ttu-id="0735f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0735f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0735f-115">name</span><span class="sxs-lookup"><span data-stu-id="0735f-115">name</span></span>|<span data-ttu-id="0735f-116">Řetězec, který určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="0735f-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0735f-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0735f-117">Child Elements</span></span>  
  
|<span data-ttu-id="0735f-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="0735f-118">Element</span></span>|<span data-ttu-id="0735f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0735f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0735f-120">\<participants ></span><span class="sxs-lookup"><span data-stu-id="0735f-120">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="0735f-121">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0735f-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0735f-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0735f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0735f-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="0735f-123">Element</span></span>|<span data-ttu-id="0735f-124">Popis</span><span class="sxs-lookup"><span data-stu-id="0735f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0735f-125">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="0735f-125">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="0735f-126">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0735f-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0735f-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0735f-127">Remarks</span></span>  
 <span data-ttu-id="0735f-128">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="0735f-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="0735f-129">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0735f-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="0735f-130">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="0735f-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="0735f-131">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="0735f-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="0735f-132">Existuje několik typů dotazu, které umožňují předplatit různé třídy <xref:System.Activities.Tracking.TrackingRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="0735f-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="0735f-133">Úplný seznam dotazů, najdete v části [ \<participants >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) a [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="0735f-133">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="0735f-134">Následující příklad ukazuje profilu sledování v konfiguračním souboru, který umožňuje sledování účastník přihlásit k odběru `Started` a `Completed` události pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0735f-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0735f-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0735f-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="0735f-136">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="0735f-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0735f-137">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="0735f-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
