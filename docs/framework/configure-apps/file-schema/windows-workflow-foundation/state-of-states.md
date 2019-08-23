---
title: <state> z <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 7c7326b2fd5ae39ca4c0f39fac05444802fa3d49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947497"
---
# <a name="state-of-states"></a><span data-ttu-id="3ca0a-102">\<Stavová > \<stavů ></span><span class="sxs-lookup"><span data-stu-id="3ca0a-102">\<state> of \<states></span></span>
<span data-ttu-id="3ca0a-103">Konfigurace element, který obsahuje informace o stavu předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="3ca0a-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3ca0a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="3ca0a-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ca0a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3ca0a-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="3ca0a-106">\<tracking></span></span>  
<span data-ttu-id="3ca0a-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="3ca0a-107">\<trackingProfile></span></span>  
<span data-ttu-id="3ca0a-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3ca0a-108">\<workflow></span></span>  
<span data-ttu-id="3ca0a-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="3ca0a-109">\<activityStateQueries></span></span>  
<span data-ttu-id="3ca0a-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="3ca0a-110">\<activityStateQuery></span></span>  
<span data-ttu-id="3ca0a-111">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="3ca0a-111">\<states></span></span>  
<span data-ttu-id="3ca0a-112">\<> stavu</span><span class="sxs-lookup"><span data-stu-id="3ca0a-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca0a-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ca0a-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ca0a-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ca0a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="3ca0a-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ca0a-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ca0a-116">Attributes</span></span>  
  
|<span data-ttu-id="3ca0a-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ca0a-117">Attribute</span></span>|<span data-ttu-id="3ca0a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="3ca0a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ca0a-119">name</span><span class="sxs-lookup"><span data-stu-id="3ca0a-119">name</span></span>|<span data-ttu-id="3ca0a-120">Řetězec, který určuje stav předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ca0a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ca0a-121">Child Elements</span></span>  
 <span data-ttu-id="3ca0a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ca0a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ca0a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ca0a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3ca0a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ca0a-124">Element</span></span>|<span data-ttu-id="3ca0a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3ca0a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ca0a-126">\<states></span><span class="sxs-lookup"><span data-stu-id="3ca0a-126">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="3ca0a-127">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ca0a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ca0a-128">Remarks</span></span>  
 <span data-ttu-id="3ca0a-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="3ca0a-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="3ca0a-131">Můžete použít [ \<argumenty >](arguments.md), [ \<stavy >](states.md) a [ \<>](states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="3ca0a-132">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="3ca0a-133">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="3ca0a-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ca0a-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ca0a-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3ca0a-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="3ca0a-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3ca0a-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="3ca0a-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
