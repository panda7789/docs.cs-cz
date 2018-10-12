---
title: '&lt;activityStateQueries&gt; služby WCF'
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 081dc297912ed5735dd51111936b85b61f463d2d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123238"
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="b7c94-102">&lt;activityStateQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="b7c94-102">&lt;activityStateQueries&gt; of WCF</span></span>

<span data-ttu-id="b7c94-103">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b7c94-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="b7c94-104">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b7c94-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="b7c94-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7c94-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="b7c94-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="b7c94-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="b7c94-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b7c94-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="b7c94-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b7c94-108">\<system.serviceModel></span></span>  
<span data-ttu-id="b7c94-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="b7c94-109">\<tracking></span></span>  
<span data-ttu-id="b7c94-110">\<profily ></span><span class="sxs-lookup"><span data-stu-id="b7c94-110">\<profiles></span></span>  
<span data-ttu-id="b7c94-111">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b7c94-111">\<trackingProfile></span></span>  
<span data-ttu-id="b7c94-112">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="b7c94-112">\<workflow></span></span>  
<span data-ttu-id="b7c94-113">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="b7c94-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="b7c94-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7c94-114">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="b7c94-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b7c94-115">Attributes and elements</span></span>

<span data-ttu-id="b7c94-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b7c94-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="b7c94-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="b7c94-117">Attributes</span></span>  

<span data-ttu-id="b7c94-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="b7c94-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="b7c94-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b7c94-119">Child elements</span></span>

|<span data-ttu-id="b7c94-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7c94-120">Element</span></span>|<span data-ttu-id="b7c94-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b7c94-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7c94-122">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="b7c94-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="b7c94-123">Dotaz, který se používá ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7c94-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b7c94-124">Pokaždé, když FaultHandler zpracovává chyby, dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="b7c94-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7c94-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="b7c94-125">Parent elements</span></span>

|<span data-ttu-id="b7c94-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7c94-126">Element</span></span>|<span data-ttu-id="b7c94-127">Popis</span><span class="sxs-lookup"><span data-stu-id="b7c94-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7c94-128">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="b7c94-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="b7c94-129">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b7c94-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b7c94-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7c94-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>    
- <xref:System.Activities.Tracking.ActivityStateQuery>    
- [<span data-ttu-id="b7c94-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b7c94-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="b7c94-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b7c94-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
