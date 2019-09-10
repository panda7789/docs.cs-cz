---
title: <trackingProfile>služby WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: c5df03d63653e658a23a36e8943c06f156d2ae00
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854937"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="61926-102">\<Profil TrackingProfile > WCF</span><span class="sxs-lookup"><span data-stu-id="61926-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="61926-103">Představuje konfigurační oddíl pro vytvoření odběru záznamů sledování pracovních postupů v účastníkovi sledování.</span><span class="sxs-lookup"><span data-stu-id="61926-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="61926-104">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="61926-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="61926-105">Definice dotazů v rámci profilu sledování oddílu definovat typy událostí, které jsou vráceny pomocí odběru.</span><span class="sxs-lookup"><span data-stu-id="61926-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="61926-106">Další informace o sledování pracovního postupu a jeho konfiguraci najdete v článku [sledování pracovních postupů](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [profily](../../../windows-workflow-foundation/tracking-profiles.md)trasování a sledování.</span><span class="sxs-lookup"><span data-stu-id="61926-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="61926-107">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="61926-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="61926-108">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="61926-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="61926-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="61926-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="61926-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="61926-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="61926-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profil TrackingProfile >**</span><span class="sxs-lookup"><span data-stu-id="61926-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61926-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61926-112">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61926-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61926-113">Attributes and Elements</span></span>  

<span data-ttu-id="61926-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61926-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61926-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="61926-115">Attributes</span></span>  
  
|<span data-ttu-id="61926-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="61926-116">Attribute</span></span>|<span data-ttu-id="61926-117">Popis</span><span class="sxs-lookup"><span data-stu-id="61926-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61926-118">name</span><span class="sxs-lookup"><span data-stu-id="61926-118">name</span></span>|<span data-ttu-id="61926-119">Řetězec, který určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="61926-119">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61926-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61926-120">Child Elements</span></span>  
  
|<span data-ttu-id="61926-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="61926-121">Element</span></span>|<span data-ttu-id="61926-122">Popis</span><span class="sxs-lookup"><span data-stu-id="61926-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61926-123">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="61926-123">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="61926-124">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="61926-124">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61926-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61926-125">Parent Elements</span></span>  
  
|<span data-ttu-id="61926-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="61926-126">Element</span></span>|<span data-ttu-id="61926-127">Popis</span><span class="sxs-lookup"><span data-stu-id="61926-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61926-128">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="61926-128">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="61926-129">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="61926-129">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61926-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61926-130">Remarks</span></span>  
 <span data-ttu-id="61926-131">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="61926-131">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="61926-132">V závislosti na vašich požadavků na monitorování, že napíšete profilu, který je velmi hrubou, který přihlásí k odběru malou sadu změn stavu vysoké úrovně v rámci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="61926-132">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="61926-133">Naopak můžete vytvořit profil velmi specifické, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="61926-133">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="61926-134">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="61926-134">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="61926-135">Existuje několik typů dotazů, které umožňují přihlášení k odběru různých tříd <xref:System.Activities.Tracking.TrackingRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="61926-135">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="61926-136">Úplný seznam dotazů najdete v tématu [ \<účastníci >](../windows-workflow-foundation/participants.md) a [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="61926-136">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="61926-137">Následující příklad ukazuje profil sledování v konfiguračním souboru, který umožňuje sledování účastníka přihlásit k odběru `Started` událostí pracovního postupu a. `Completed`</span><span class="sxs-lookup"><span data-stu-id="61926-137">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="61926-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61926-138">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="61926-139">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="61926-139">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="61926-140">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="61926-140">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
