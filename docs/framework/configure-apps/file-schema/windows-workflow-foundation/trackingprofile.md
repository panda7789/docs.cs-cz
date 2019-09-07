---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 3120d6f5d1bb5a5cf452567e96766231534f3f41
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398591"
---
# <a name="trackingprofile"></a><span data-ttu-id="e29b7-101">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e29b7-101">\<trackingProfile></span></span>
<span data-ttu-id="e29b7-102">Představuje konfigurační oddíl pro vytvoření odběru záznamů sledování pracovních postupů v účastníkovi sledování.</span><span class="sxs-lookup"><span data-stu-id="e29b7-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="e29b7-103">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="e29b7-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e29b7-104">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="e29b7-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="e29b7-105">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v článku [sledování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [profily](../../../windows-workflow-foundation/tracking-profiles.md)trasování a sledování.</span><span class="sxs-lookup"><span data-stu-id="e29b7-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e29b7-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e29b7-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e29b7-107">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e29b7-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e29b7-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e29b7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e29b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profil TrackingProfile >**</span><span class="sxs-lookup"><span data-stu-id="e29b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e29b7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e29b7-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e29b7-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e29b7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e29b7-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e29b7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e29b7-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e29b7-113">Attributes</span></span>  
  
|<span data-ttu-id="e29b7-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="e29b7-114">Attribute</span></span>|<span data-ttu-id="e29b7-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e29b7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e29b7-116">name</span><span class="sxs-lookup"><span data-stu-id="e29b7-116">name</span></span>|<span data-ttu-id="e29b7-117">Řetězec, který určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="e29b7-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e29b7-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e29b7-118">Child Elements</span></span>  
  
|<span data-ttu-id="e29b7-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e29b7-119">Element</span></span>|<span data-ttu-id="e29b7-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e29b7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e29b7-121">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="e29b7-121">\<participants></span></span>](participants.md)|<span data-ttu-id="e29b7-122">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e29b7-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e29b7-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e29b7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e29b7-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="e29b7-124">Element</span></span>|<span data-ttu-id="e29b7-125">Popis</span><span class="sxs-lookup"><span data-stu-id="e29b7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e29b7-126">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e29b7-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="e29b7-127">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e29b7-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e29b7-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e29b7-128">Remarks</span></span>  
 <span data-ttu-id="e29b7-129">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="e29b7-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="e29b7-130">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e29b7-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="e29b7-131">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="e29b7-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="e29b7-132">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="e29b7-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="e29b7-133">Existuje několik typů dotazů, které umožňují přihlášení k odběru různých tříd <xref:System.Activities.Tracking.TrackingRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="e29b7-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="e29b7-134">Úplný seznam dotazů najdete v tématu [ \<účastníci >](participants.md) a [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e29b7-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="e29b7-135">Následující příklad ukazuje profil sledování v konfiguračním souboru, který umožňuje sledování účastníka přihlásit k odběru `Started` událostí pracovního postupu a. `Completed`</span><span class="sxs-lookup"><span data-stu-id="e29b7-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e29b7-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e29b7-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="e29b7-137">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e29b7-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e29b7-138">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="e29b7-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
