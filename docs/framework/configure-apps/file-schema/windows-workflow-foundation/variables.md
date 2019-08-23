---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 563ce96f61bbb39f1590ca0f43c163ea2d3d7961
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947246"
---
# <a name="variables"></a><span data-ttu-id="60642-101">\<> proměnných</span><span class="sxs-lookup"><span data-stu-id="60642-101">\<variables></span></span>
<span data-ttu-id="60642-102">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="60642-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="60642-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="60642-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="60642-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="60642-104">\<system.serviceModel></span></span>  
<span data-ttu-id="60642-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="60642-105">\<tracking></span></span>  
<span data-ttu-id="60642-106">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="60642-106">\<trackingProfile></span></span>  
<span data-ttu-id="60642-107">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="60642-107">\<workflow></span></span>  
<span data-ttu-id="60642-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="60642-108">\<activityStateQueries></span></span>  
<span data-ttu-id="60642-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="60642-109">\<activityStateQuery></span></span>  
<span data-ttu-id="60642-110">\<> proměnných</span><span class="sxs-lookup"><span data-stu-id="60642-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60642-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60642-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60642-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60642-112">Attributes and Elements</span></span>  
 <span data-ttu-id="60642-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60642-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60642-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="60642-114">Attributes</span></span>  
 <span data-ttu-id="60642-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="60642-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60642-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60642-116">Child Elements</span></span>  
  
|<span data-ttu-id="60642-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="60642-117">Element</span></span>|<span data-ttu-id="60642-118">Popis</span><span class="sxs-lookup"><span data-stu-id="60642-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60642-119">\<> proměnných</span><span class="sxs-lookup"><span data-stu-id="60642-119">\<variable></span></span>](variable.md)|<span data-ttu-id="60642-120">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="60642-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60642-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60642-121">Parent Elements</span></span>  
  
|<span data-ttu-id="60642-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="60642-122">Element</span></span>|<span data-ttu-id="60642-123">Popis</span><span class="sxs-lookup"><span data-stu-id="60642-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60642-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="60642-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="60642-125">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="60642-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="60642-126">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="60642-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60642-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60642-127">Remarks</span></span>  
 <span data-ttu-id="60642-128">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="60642-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="60642-129">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="60642-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="60642-130">Můžete použít [ \<argumenty >](arguments.md), [ \<stavy >](states.md) a [ \<>](states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="60642-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="60642-131">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="60642-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="60642-132">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="60642-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60642-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60642-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="60642-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="60642-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="60642-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="60642-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
