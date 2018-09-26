---
title: '&lt;Pracovní postup&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: 940d396bd6e3dc3cdc5d8fb6f72d293061f3aa0e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112345"
---
# <a name="ltworkflowgt"></a><span data-ttu-id="7d5f4-102">&lt;Pracovní postup&gt;</span><span class="sxs-lookup"><span data-stu-id="7d5f4-102">&lt;workflow&gt;</span></span>
<span data-ttu-id="7d5f4-103">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-103">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="7d5f4-104">Další informace v sledování pracovních postupů a jeho konfiguraci najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7d5f4-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7d5f4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d5f4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7d5f4-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-106">\<tracking></span></span>  
<span data-ttu-id="7d5f4-107">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-107">\<trackingProfile></span></span>  
<span data-ttu-id="7d5f4-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-108">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d5f4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d5f4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d5f4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d5f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d5f4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d5f4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d5f4-112">Attributes</span></span>  
  
|<span data-ttu-id="7d5f4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d5f4-113">Attribute</span></span>|<span data-ttu-id="7d5f4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7d5f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d5f4-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="7d5f4-115">activityDefinitionId</span></span>|<span data-ttu-id="7d5f4-116">Řetězec, který určuje ID definice aktivity pracovního postupu sledován.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d5f4-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d5f4-117">Child Elements</span></span>  
  
|<span data-ttu-id="7d5f4-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d5f4-118">Element</span></span>|<span data-ttu-id="7d5f4-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7d5f4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d5f4-120">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-120">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="7d5f4-121">Představuje kolekci dotazů, které se používají ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7d5f4-122">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záznamů aktivit naplánována.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="7d5f4-123">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-123">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="7d5f4-124">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="7d5f4-125">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="7d5f4-126">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="7d5f4-127">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="7d5f4-128">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7d5f4-128">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="7d5f4-129">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7d5f4-130">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="7d5f4-131">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-131">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="7d5f4-132">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7d5f4-133">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="7d5f4-134">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-134">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="7d5f4-135">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="7d5f4-136">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="7d5f4-137">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="7d5f4-137">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="7d5f4-138">Představuje kolekci dotazů, které se používají ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="7d5f4-139">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="7d5f4-140">Takový dotaz byste měli používat ke sledování zpracování chyb, k nimž došlo v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="7d5f4-141">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru chyby šíření hodnoty záznamů.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="7d5f4-142">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-142">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="7d5f4-143">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d5f4-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d5f4-144">Parent Elements</span></span>  
  
|<span data-ttu-id="7d5f4-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d5f4-145">Element</span></span>|<span data-ttu-id="7d5f4-146">Popis</span><span class="sxs-lookup"><span data-stu-id="7d5f4-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d5f4-147">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7d5f4-147">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="7d5f4-148">Představuje konfigurační oddíl pro vytváření odběru sledování záznamů v sledování účastník pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="7d5f4-149">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="7d5f4-150">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d5f4-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d5f4-151">Remarks</span></span>  
 <span data-ttu-id="7d5f4-152">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance určitý pracovní postup za běhu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="7d5f4-153">Instance pracovního postupu sledované je identifikován tento element konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="7d5f4-154">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="7d5f4-155">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="7d5f4-156">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="7d5f4-157">Existuje několik typů dotazu, které umožňují že předplatit různé třídy sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="7d5f4-158">Úplný seznam dotazů, najdete v seznamu podřízených prvků tohoto tématu a [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7d5f4-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="7d5f4-159">Následující příklad ukazuje profilu sledování v konfiguračním souboru, který umožňuje sledování účastník přihlásit k odběru `Started` a `Completed` události pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7d5f4-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d5f4-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d5f4-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="7d5f4-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7d5f4-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7d5f4-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="7d5f4-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
