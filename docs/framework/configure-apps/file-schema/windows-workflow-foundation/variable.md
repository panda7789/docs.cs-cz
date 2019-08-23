---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: a8f66f950db1edf8cd6ec21400785fb7e01b878e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947266"
---
# <a name="variable"></a><span data-ttu-id="bf453-101">\<> proměnných</span><span class="sxs-lookup"><span data-stu-id="bf453-101">\<variable></span></span>
<span data-ttu-id="bf453-102">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf453-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="bf453-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bf453-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="bf453-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bf453-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bf453-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="bf453-105">\<tracking></span></span>  
<span data-ttu-id="bf453-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="bf453-106">\<profiles></span></span>  
<span data-ttu-id="bf453-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bf453-107">\<trackingProfile></span></span>  
<span data-ttu-id="bf453-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf453-108">\<workflow></span></span>  
<span data-ttu-id="bf453-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="bf453-109">\<activityStateQueries></span></span>  
<span data-ttu-id="bf453-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="bf453-110">\<activityStateQuery></span></span>  
<span data-ttu-id="bf453-111">\<> proměnných</span><span class="sxs-lookup"><span data-stu-id="bf453-111">\<variables></span></span>  
<span data-ttu-id="bf453-112">\<> proměnných</span><span class="sxs-lookup"><span data-stu-id="bf453-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf453-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf453-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf453-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bf453-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bf453-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bf453-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf453-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="bf453-116">Attributes</span></span>  
  
|<span data-ttu-id="bf453-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf453-117">Attribute</span></span>|<span data-ttu-id="bf453-118">Popis</span><span class="sxs-lookup"><span data-stu-id="bf453-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf453-119">name</span><span class="sxs-lookup"><span data-stu-id="bf453-119">name</span></span>|<span data-ttu-id="bf453-120">Řetězec, který určuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="bf453-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf453-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bf453-121">Child Elements</span></span>  
 <span data-ttu-id="bf453-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf453-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf453-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bf453-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf453-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf453-124">Element</span></span>|<span data-ttu-id="bf453-125">Popis</span><span class="sxs-lookup"><span data-stu-id="bf453-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf453-126">\<> proměnných</span><span class="sxs-lookup"><span data-stu-id="bf453-126">\<variable></span></span>](variable.md)|<span data-ttu-id="bf453-127">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf453-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf453-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf453-128">Remarks</span></span>  
 <span data-ttu-id="bf453-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bf453-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="bf453-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="bf453-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="bf453-131">Můžete použít [ \<argumenty >](arguments.md), [ \<stavy >](states.md) a [ \<>](states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="bf453-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="bf453-132">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf453-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="bf453-133">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="bf453-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf453-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf453-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bf453-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bf453-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bf453-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="bf453-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
