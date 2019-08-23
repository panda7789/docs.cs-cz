---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 560df771b44fc8ba8d192657677bf0496283b539
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945431"
---
# <a name="activitystatequery"></a><span data-ttu-id="7eb46-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="7eb46-101">\<activityStateQuery></span></span>
<span data-ttu-id="7eb46-102">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7eb46-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="7eb46-103">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7eb46-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="7eb46-104">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7eb46-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="7eb46-105">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="7eb46-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="7eb46-106">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7eb46-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7eb46-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7eb46-107">\<system.serviceModel></span></span>  
<span data-ttu-id="7eb46-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="7eb46-108">\<tracking></span></span>  
<span data-ttu-id="7eb46-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7eb46-109">\<trackingProfile></span></span>  
<span data-ttu-id="7eb46-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="7eb46-110">\<workflow></span></span>  
<span data-ttu-id="7eb46-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="7eb46-111">\<activityStateQueries></span></span>  
<span data-ttu-id="7eb46-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="7eb46-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb46-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb46-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eb46-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7eb46-114">Attributes and Elements</span></span>  
 <span data-ttu-id="7eb46-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7eb46-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eb46-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="7eb46-116">Attributes</span></span>  
  
|<span data-ttu-id="7eb46-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="7eb46-117">Attribute</span></span>|<span data-ttu-id="7eb46-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7eb46-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7eb46-119">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="7eb46-119">activityName</span></span>|<span data-ttu-id="7eb46-120">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="7eb46-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eb46-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7eb46-121">Child Elements</span></span>  
  
|<span data-ttu-id="7eb46-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7eb46-122">Element</span></span>|<span data-ttu-id="7eb46-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7eb46-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eb46-124">\<arguments></span><span class="sxs-lookup"><span data-stu-id="7eb46-124">\<arguments></span></span>](arguments.md)|<span data-ttu-id="7eb46-125">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7eb46-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="7eb46-126">\<states></span><span class="sxs-lookup"><span data-stu-id="7eb46-126">\<states></span></span>](states.md)|<span data-ttu-id="7eb46-127">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="7eb46-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="7eb46-128">\<states></span><span class="sxs-lookup"><span data-stu-id="7eb46-128">\<states></span></span>](states.md)|<span data-ttu-id="7eb46-129">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="7eb46-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7eb46-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7eb46-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7eb46-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="7eb46-131">Element</span></span>|<span data-ttu-id="7eb46-132">Popis</span><span class="sxs-lookup"><span data-stu-id="7eb46-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eb46-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="7eb46-133">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="7eb46-134">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="7eb46-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7eb46-135">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="7eb46-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eb46-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7eb46-136">Remarks</span></span>  
 <span data-ttu-id="7eb46-137">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7eb46-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="7eb46-138">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="7eb46-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="7eb46-139">Můžete použít [ \<argumenty >](arguments.md), [ \<stavy >](states.md) a [ \<>](states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="7eb46-139">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="7eb46-140">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="7eb46-140">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="7eb46-141">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="7eb46-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7eb46-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7eb46-142">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7eb46-143">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7eb46-143">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7eb46-144">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="7eb46-144">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
