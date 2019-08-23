---
title: <activityStateQueries>služby WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 415cd4a75ecab725f91bcd298f8a7966ea6079d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920301"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="a64e8-102">\<activityStateQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="a64e8-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="a64e8-103">Představuje kolekci dotazů, které se používají ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a64e8-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a64e8-104">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a64e8-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a64e8-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="a64e8-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a64e8-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="a64e8-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="a64e8-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a64e8-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="a64e8-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a64e8-108">\<system.serviceModel></span></span>  
<span data-ttu-id="a64e8-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a64e8-109">\<tracking></span></span>  
<span data-ttu-id="a64e8-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="a64e8-110">\<profiles></span></span>  
<span data-ttu-id="a64e8-111">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a64e8-111">\<trackingProfile></span></span>  
<span data-ttu-id="a64e8-112">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a64e8-112">\<workflow></span></span>  
<span data-ttu-id="a64e8-113">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="a64e8-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="a64e8-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a64e8-114">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="a64e8-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a64e8-115">Attributes and elements</span></span>

<span data-ttu-id="a64e8-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a64e8-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="a64e8-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="a64e8-117">Attributes</span></span>  

<span data-ttu-id="a64e8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a64e8-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="a64e8-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a64e8-119">Child elements</span></span>

|<span data-ttu-id="a64e8-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a64e8-120">Element</span></span>|<span data-ttu-id="a64e8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a64e8-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a64e8-122">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="a64e8-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="a64e8-123">Dotaz, který se používá ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="a64e8-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a64e8-124">K této události dochází pokaždé, když když FaultHandler zpracovává chybu.</span><span class="sxs-lookup"><span data-stu-id="a64e8-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a64e8-125">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a64e8-125">Parent elements</span></span>

|<span data-ttu-id="a64e8-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="a64e8-126">Element</span></span>|<span data-ttu-id="a64e8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="a64e8-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a64e8-128">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a64e8-128">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a64e8-129">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a64e8-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a64e8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a64e8-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="a64e8-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a64e8-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a64e8-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a64e8-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
