---
title: <states> z <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 50827577374859133e6c673e8850e145b4ccab73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947430"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="b5d86-102">\<stavy > \<> ActivityStateQuery</span><span class="sxs-lookup"><span data-stu-id="b5d86-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="b5d86-103">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="b5d86-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="b5d86-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b5d86-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b5d86-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b5d86-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b5d86-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="b5d86-106">\<tracking></span></span>  
<span data-ttu-id="b5d86-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b5d86-107">\<trackingProfile></span></span>  
<span data-ttu-id="b5d86-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b5d86-108">\<workflow></span></span>  
<span data-ttu-id="b5d86-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b5d86-109">\<activityStateQueries></span></span>  
<span data-ttu-id="b5d86-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b5d86-110">\<activityStateQuery></span></span>  
<span data-ttu-id="b5d86-111">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="b5d86-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5d86-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5d86-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5d86-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b5d86-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b5d86-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b5d86-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5d86-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="b5d86-115">Attributes</span></span>  
 <span data-ttu-id="b5d86-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="b5d86-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b5d86-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b5d86-117">Child Elements</span></span>  
  
|<span data-ttu-id="b5d86-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="b5d86-118">Element</span></span>|<span data-ttu-id="b5d86-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b5d86-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5d86-120">\<> stavu</span><span class="sxs-lookup"><span data-stu-id="b5d86-120">\<state></span></span>](state-of-states.md)|<span data-ttu-id="b5d86-121">Konfigurace element, který obsahuje stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="b5d86-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5d86-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b5d86-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b5d86-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b5d86-123">Element</span></span>|<span data-ttu-id="b5d86-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b5d86-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5d86-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b5d86-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="b5d86-126">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="b5d86-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b5d86-127">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="b5d86-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5d86-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5d86-128">Remarks</span></span>  
 <span data-ttu-id="b5d86-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b5d86-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b5d86-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="b5d86-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b5d86-131">Můžete použít [ \<argumenty >](arguments.md), [ \<stavy >](states.md) a [ \<>](states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b5d86-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b5d86-132">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="b5d86-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b5d86-133">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="b5d86-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5d86-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5d86-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b5d86-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b5d86-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b5d86-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b5d86-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
