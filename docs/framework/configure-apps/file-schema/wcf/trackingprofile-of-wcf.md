---
title: '&lt;trackingProfile&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: 7f1b6836dc8d9d4e56a0a6831a373e50bbae920c
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839706"
---
# <a name="lttrackingprofilegt-of-wcf"></a><span data-ttu-id="dc313-102">&lt;trackingProfile&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="dc313-102">&lt;trackingProfile&gt; of WCF</span></span>
<span data-ttu-id="dc313-103">Představuje konfigurační oddíl pro vytváření odběru sledování záznamů v sledování účastník pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dc313-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="dc313-104">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="dc313-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="dc313-105">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="dc313-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="dc313-106">Další informace v sledování pracovních postupů a jeho konfiguraci najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dc313-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="dc313-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dc313-107">\<system.serviceModel></span></span>  
<span data-ttu-id="dc313-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="dc313-108">\<tracking></span></span>  
<span data-ttu-id="dc313-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="dc313-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc313-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc313-110">Syntax</span></span>  
  
```xml
   <system.serviceModel>  <tracking>      <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>    
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc313-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc313-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dc313-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc313-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc313-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc313-113">Attributes</span></span>  
  
|<span data-ttu-id="dc313-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="dc313-114">Attribute</span></span>|<span data-ttu-id="dc313-115">Popis</span><span class="sxs-lookup"><span data-stu-id="dc313-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc313-116">name</span><span class="sxs-lookup"><span data-stu-id="dc313-116">name</span></span>|<span data-ttu-id="dc313-117">Řetězec, který určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="dc313-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc313-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc313-118">Child Elements</span></span>  
  
|<span data-ttu-id="dc313-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc313-119">Element</span></span>|<span data-ttu-id="dc313-120">Popis</span><span class="sxs-lookup"><span data-stu-id="dc313-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc313-121">\<participants ></span><span class="sxs-lookup"><span data-stu-id="dc313-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="dc313-122">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc313-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc313-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc313-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dc313-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc313-124">Element</span></span>|<span data-ttu-id="dc313-125">Popis</span><span class="sxs-lookup"><span data-stu-id="dc313-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc313-126">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="dc313-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="dc313-127">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dc313-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc313-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc313-128">Remarks</span></span>  
 <span data-ttu-id="dc313-129">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="dc313-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="dc313-130">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dc313-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="dc313-131">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="dc313-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="dc313-132">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="dc313-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="dc313-133">Existuje několik typů dotazu, které umožňují předplatit různé třídy <xref:System.Activities.Tracking.TrackingRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="dc313-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="dc313-134">Úplný seznam dotazů, najdete v části [ \<participants >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) a [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="dc313-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="dc313-135">Následující příklad ukazuje profilu sledování v konfiguračním souboru, který umožňuje sledování účastník přihlásit k odběru `Started` a `Completed` události pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dc313-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc313-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc313-136">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="dc313-137">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="dc313-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="dc313-138">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="dc313-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
