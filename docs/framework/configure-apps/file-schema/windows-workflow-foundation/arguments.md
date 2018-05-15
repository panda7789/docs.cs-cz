---
title: '&lt;Argumenty&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: ae2fd4a05cc8ca93cd74ccceb08a7a077b504f0c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltargumentsgt"></a><span data-ttu-id="d7fc6-102">&lt;Argumenty&gt;</span><span class="sxs-lookup"><span data-stu-id="d7fc6-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="d7fc6-103">Představuje kolekci argumentů přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="d7fc6-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d7fc6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d7fc6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d7fc6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d7fc6-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-106">\<tracking></span></span>  
<span data-ttu-id="d7fc6-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-107">\<trackingProfile></span></span>  
<span data-ttu-id="d7fc6-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-108">\<workflow></span></span>  
<span data-ttu-id="d7fc6-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-109">\<activityStateQueries></span></span>  
<span data-ttu-id="d7fc6-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-110">\<activityStateQuery></span></span>  
<span data-ttu-id="d7fc6-111">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7fc6-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7fc6-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7fc6-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d7fc6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d7fc6-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7fc6-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="d7fc6-115">Attributes</span></span>  
 <span data-ttu-id="d7fc6-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="d7fc6-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7fc6-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d7fc6-117">Child Elements</span></span>  
  
|<span data-ttu-id="d7fc6-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="d7fc6-118">Element</span></span>|<span data-ttu-id="d7fc6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d7fc6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7fc6-120">\<argument ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="d7fc6-121">Argument přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7fc6-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d7fc6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d7fc6-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d7fc6-123">Element</span></span>|<span data-ttu-id="d7fc6-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d7fc6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7fc6-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="d7fc6-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="d7fc6-126">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d7fc6-127">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7fc6-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7fc6-128">Remarks</span></span>  
 <span data-ttu-id="d7fc6-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d7fc6-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d7fc6-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="d7fc6-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d7fc6-132">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d7fc6-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7fc6-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7fc6-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="d7fc6-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d7fc6-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d7fc6-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d7fc6-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
