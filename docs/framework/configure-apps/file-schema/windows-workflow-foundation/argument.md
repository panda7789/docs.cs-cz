---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: f2aeb61e2e72f5bd6a696c031279f2c57907166b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946156"
---
# <a name="argument"></a><span data-ttu-id="449e5-101">\<argument></span><span class="sxs-lookup"><span data-stu-id="449e5-101">\<argument></span></span>
<span data-ttu-id="449e5-102">Konfigurace element, který představuje argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="449e5-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="449e5-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="449e5-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="449e5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="449e5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="449e5-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="449e5-105">\<tracking></span></span>  
<span data-ttu-id="449e5-106">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="449e5-106">\<trackingProfile></span></span>  
<span data-ttu-id="449e5-107">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="449e5-107">\<workflow></span></span>  
<span data-ttu-id="449e5-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="449e5-108">\<activityStateQueries></span></span>  
<span data-ttu-id="449e5-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="449e5-109">\<activityStateQuery></span></span>  
<span data-ttu-id="449e5-110">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="449e5-110">\<arguments></span></span>  
<span data-ttu-id="449e5-111">\<argument></span><span class="sxs-lookup"><span data-stu-id="449e5-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="449e5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="449e5-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="449e5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="449e5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="449e5-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="449e5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="449e5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="449e5-115">Attributes</span></span>  
  
|<span data-ttu-id="449e5-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="449e5-116">Attribute</span></span>|<span data-ttu-id="449e5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="449e5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="449e5-118">name</span><span class="sxs-lookup"><span data-stu-id="449e5-118">name</span></span>|<span data-ttu-id="449e5-119">Řetězec, který určuje název argumentu.</span><span class="sxs-lookup"><span data-stu-id="449e5-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="449e5-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="449e5-120">Child Elements</span></span>  
 <span data-ttu-id="449e5-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="449e5-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="449e5-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="449e5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="449e5-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="449e5-123">Element</span></span>|<span data-ttu-id="449e5-124">Popis</span><span class="sxs-lookup"><span data-stu-id="449e5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="449e5-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="449e5-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="449e5-126">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="449e5-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="449e5-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="449e5-127">Remarks</span></span>  
 <span data-ttu-id="449e5-128">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="449e5-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="449e5-129">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="449e5-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="449e5-130">Můžete použít [ \<argumenty >](arguments.md), [ \<stavy >](states.md) a [ \<>](states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="449e5-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="449e5-131">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="449e5-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="449e5-132">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="449e5-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="449e5-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="449e5-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="449e5-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="449e5-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="449e5-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="449e5-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
