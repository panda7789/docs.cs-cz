---
title: '&lt;TrackingProfile&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 245a7c759f217bcf85c6d1b3d7dd13dd845fd0e4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757317"
---
# <a name="lttrackingprofilegt"></a><span data-ttu-id="96a54-102">&lt;TrackingProfile&gt;</span><span class="sxs-lookup"><span data-stu-id="96a54-102">&lt;trackingProfile&gt;</span></span>
<span data-ttu-id="96a54-103">Představuje konfigurační oddíl pro vytváření odběru sledování záznamů v sledování účastník pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="96a54-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="96a54-104">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="96a54-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="96a54-105">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="96a54-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="96a54-106">Další informace v pracovním postupu sledování a jeho konfigurace najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="96a54-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="96a54-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96a54-107">\<system.serviceModel></span></span>  
<span data-ttu-id="96a54-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="96a54-108">\<tracking></span></span>  
<span data-ttu-id="96a54-109">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="96a54-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a54-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96a54-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96a54-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96a54-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96a54-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96a54-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96a54-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="96a54-113">Attributes</span></span>  
  
|<span data-ttu-id="96a54-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="96a54-114">Attribute</span></span>|<span data-ttu-id="96a54-115">Popis</span><span class="sxs-lookup"><span data-stu-id="96a54-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96a54-116">name</span><span class="sxs-lookup"><span data-stu-id="96a54-116">name</span></span>|<span data-ttu-id="96a54-117">Řetězec, který určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="96a54-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96a54-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96a54-118">Child Elements</span></span>  
  
|<span data-ttu-id="96a54-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="96a54-119">Element</span></span>|<span data-ttu-id="96a54-120">Popis</span><span class="sxs-lookup"><span data-stu-id="96a54-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96a54-121">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="96a54-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="96a54-122">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **hypertextový odkaz "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="96a54-122">A configuration element that contains all queries for a specific workflow identified by the **a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx"ctivityDefinitionId** property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96a54-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96a54-123">Parent Elements</span></span>  
  
|<span data-ttu-id="96a54-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="96a54-124">Element</span></span>|<span data-ttu-id="96a54-125">Popis</span><span class="sxs-lookup"><span data-stu-id="96a54-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96a54-126">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="96a54-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="96a54-127">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="96a54-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96a54-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96a54-128">Remarks</span></span>  
 <span data-ttu-id="96a54-129">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="96a54-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="96a54-130">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="96a54-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="96a54-131">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="96a54-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="96a54-132">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="96a54-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="96a54-133">Existuje několik typy dotazů, které umožňují přihlášení k odběru pro různé třídy HYPERLINK "http://msdn.microsoft.com/library/system.activities.tracking.trackingrecord(VS.100).aspx" TrackingRecord objekty.</span><span class="sxs-lookup"><span data-stu-id="96a54-133">There are a handful of query types that allow you subscribe to different classes of  HYPERLINK "http://msdn.microsoft.com/library/system.activities.tracking.trackingrecord(VS.100).aspx" TrackingRecord objects.</span></span> <span data-ttu-id="96a54-134">Úplný seznam dotazů najdete v tématu [ \<účastníky >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) a [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="96a54-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="96a54-135">Následující příklad ukazuje profil sledování v konfiguračním souboru, který umožňuje účastníkem sledování pro přihlášení k odběru `Started` a `Completed` události pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="96a54-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96a54-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="96a54-136">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="96a54-137">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="96a54-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="96a54-138">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="96a54-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
