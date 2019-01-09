---
title: '&lt;activityStateQueries&gt; služby WCF'
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 2dabfdd248006de60b5e84e739f78e03f364dde3
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146183"
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="be110-102">&lt;activityStateQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="be110-102">&lt;activityStateQueries&gt; of WCF</span></span>

<span data-ttu-id="be110-103">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="be110-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="be110-104">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="be110-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="be110-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="be110-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="be110-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="be110-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="be110-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="be110-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="be110-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="be110-108">\<system.serviceModel></span></span>  
<span data-ttu-id="be110-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="be110-109">\<tracking></span></span>  
<span data-ttu-id="be110-110">\<profily ></span><span class="sxs-lookup"><span data-stu-id="be110-110">\<profiles></span></span>  
<span data-ttu-id="be110-111">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="be110-111">\<trackingProfile></span></span>  
<span data-ttu-id="be110-112">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="be110-112">\<workflow></span></span>  
<span data-ttu-id="be110-113">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="be110-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="be110-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be110-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
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
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="be110-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="be110-115">Attributes and elements</span></span>

<span data-ttu-id="be110-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="be110-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="be110-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="be110-117">Attributes</span></span>  

<span data-ttu-id="be110-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="be110-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="be110-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="be110-119">Child elements</span></span>

|<span data-ttu-id="be110-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="be110-120">Element</span></span>|<span data-ttu-id="be110-121">Popis</span><span class="sxs-lookup"><span data-stu-id="be110-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be110-122">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="be110-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="be110-123">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="be110-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="be110-124">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="be110-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="be110-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="be110-125">Parent elements</span></span>

|<span data-ttu-id="be110-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="be110-126">Element</span></span>|<span data-ttu-id="be110-127">Popis</span><span class="sxs-lookup"><span data-stu-id="be110-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be110-128">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="be110-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="be110-129">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="be110-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="be110-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be110-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>    
- <xref:System.Activities.Tracking.ActivityStateQuery>    
- [<span data-ttu-id="be110-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="be110-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="be110-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="be110-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
