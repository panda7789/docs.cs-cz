---
title: "&lt;Proměnná&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3db57b3332638092fc9f16de5199b65c4efafebd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltvariablegt"></a><span data-ttu-id="9d00a-102">&lt;Proměnná&gt;</span><span class="sxs-lookup"><span data-stu-id="9d00a-102">&lt;variable&gt;</span></span>
<span data-ttu-id="9d00a-103">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="9d00a-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="9d00a-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9d00a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9d00a-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9d00a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9d00a-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9d00a-106">\<tracking></span></span>  
<span data-ttu-id="9d00a-107">\<profily ></span><span class="sxs-lookup"><span data-stu-id="9d00a-107">\<profiles></span></span>  
<span data-ttu-id="9d00a-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9d00a-108">\<trackingProfile></span></span>  
<span data-ttu-id="9d00a-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9d00a-109">\<workflow></span></span>  
<span data-ttu-id="9d00a-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="9d00a-110">\<activityStateQueries></span></span>  
<span data-ttu-id="9d00a-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="9d00a-111">\<activityStateQuery></span></span>  
<span data-ttu-id="9d00a-112">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="9d00a-112">\<variables></span></span>  
<span data-ttu-id="9d00a-113">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="9d00a-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d00a-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d00a-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d00a-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d00a-115">Attributes and Elements</span></span>  
 <span data-ttu-id="9d00a-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d00a-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d00a-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d00a-117">Attributes</span></span>  
  
|<span data-ttu-id="9d00a-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d00a-118">Attribute</span></span>|<span data-ttu-id="9d00a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9d00a-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d00a-120">name</span><span class="sxs-lookup"><span data-stu-id="9d00a-120">name</span></span>|<span data-ttu-id="9d00a-121">Řetězec, který určuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="9d00a-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d00a-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d00a-122">Child Elements</span></span>  
 <span data-ttu-id="9d00a-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="9d00a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d00a-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d00a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9d00a-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d00a-125">Element</span></span>|<span data-ttu-id="9d00a-126">Popis</span><span class="sxs-lookup"><span data-stu-id="9d00a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d00a-127">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="9d00a-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="9d00a-128">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="9d00a-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d00a-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d00a-129">Remarks</span></span>  
 <span data-ttu-id="9d00a-130">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9d00a-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="9d00a-131">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="9d00a-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="9d00a-132">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="9d00a-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="9d00a-133">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="9d00a-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d00a-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d00a-134">See Also</span></span>  
 <span data-ttu-id="9d00a-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9d00a-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9d00a-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9d00a-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="9d00a-137">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="9d00a-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9d00a-138">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="9d00a-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
