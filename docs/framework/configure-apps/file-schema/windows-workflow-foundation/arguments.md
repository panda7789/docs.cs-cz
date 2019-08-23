---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: bb7ae702209df3c0297ec2cfac6b09ee47ad9558
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946133"
---
# <a name="arguments"></a><span data-ttu-id="d47d4-101">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="d47d4-101">\<arguments></span></span>
<span data-ttu-id="d47d4-102">Představuje kolekci argumentů přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d47d4-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="d47d4-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d47d4-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d47d4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d47d4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d47d4-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d47d4-105">\<tracking></span></span>  
<span data-ttu-id="d47d4-106">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d47d4-106">\<trackingProfile></span></span>  
<span data-ttu-id="d47d4-107">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d47d4-107">\<workflow></span></span>  
<span data-ttu-id="d47d4-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="d47d4-108">\<activityStateQueries></span></span>  
<span data-ttu-id="d47d4-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d47d4-109">\<activityStateQuery></span></span>  
<span data-ttu-id="d47d4-110">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="d47d4-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d47d4-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d47d4-111">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d47d4-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d47d4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d47d4-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d47d4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d47d4-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d47d4-114">Attributes</span></span>  
 <span data-ttu-id="d47d4-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="d47d4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d47d4-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d47d4-116">Child Elements</span></span>  
  
|<span data-ttu-id="d47d4-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d47d4-117">Element</span></span>|<span data-ttu-id="d47d4-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d47d4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d47d4-119">\<argument></span><span class="sxs-lookup"><span data-stu-id="d47d4-119">\<argument></span></span>](argument.md)|<span data-ttu-id="d47d4-120">Argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d47d4-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d47d4-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d47d4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d47d4-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d47d4-122">Element</span></span>|<span data-ttu-id="d47d4-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d47d4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d47d4-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d47d4-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="d47d4-125">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="d47d4-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d47d4-126">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="d47d4-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d47d4-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d47d4-127">Remarks</span></span>  
 <span data-ttu-id="d47d4-128">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d47d4-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d47d4-129">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="d47d4-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d47d4-130">Můžete použít [ \<argumenty >](arguments.md), [ \<stavy >](states.md) a [ \<>](states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="d47d4-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d47d4-131">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="d47d4-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d47d4-132">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d47d4-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d47d4-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d47d4-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d47d4-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d47d4-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d47d4-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d47d4-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
