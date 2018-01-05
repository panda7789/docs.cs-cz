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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 971e3e366c2383828dde8e8f152660fb39c886ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltvariablegt"></a><span data-ttu-id="b8c05-102">&lt;Proměnná&gt;</span><span class="sxs-lookup"><span data-stu-id="b8c05-102">&lt;variable&gt;</span></span>
<span data-ttu-id="b8c05-103">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="b8c05-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="b8c05-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b8c05-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b8c05-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b8c05-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b8c05-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="b8c05-106">\<tracking></span></span>  
<span data-ttu-id="b8c05-107">\<profily ></span><span class="sxs-lookup"><span data-stu-id="b8c05-107">\<profiles></span></span>  
<span data-ttu-id="b8c05-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b8c05-108">\<trackingProfile></span></span>  
<span data-ttu-id="b8c05-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="b8c05-109">\<workflow></span></span>  
<span data-ttu-id="b8c05-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="b8c05-110">\<activityStateQueries></span></span>  
<span data-ttu-id="b8c05-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="b8c05-111">\<activityStateQuery></span></span>  
<span data-ttu-id="b8c05-112">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="b8c05-112">\<variables></span></span>  
<span data-ttu-id="b8c05-113">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="b8c05-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c05-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8c05-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8c05-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b8c05-115">Attributes and Elements</span></span>  
 <span data-ttu-id="b8c05-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b8c05-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8c05-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="b8c05-117">Attributes</span></span>  
  
|<span data-ttu-id="b8c05-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="b8c05-118">Attribute</span></span>|<span data-ttu-id="b8c05-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b8c05-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8c05-120">name</span><span class="sxs-lookup"><span data-stu-id="b8c05-120">name</span></span>|<span data-ttu-id="b8c05-121">Řetězec, který určuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="b8c05-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8c05-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b8c05-122">Child Elements</span></span>  
 <span data-ttu-id="b8c05-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8c05-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8c05-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b8c05-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b8c05-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8c05-125">Element</span></span>|<span data-ttu-id="b8c05-126">Popis</span><span class="sxs-lookup"><span data-stu-id="b8c05-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8c05-127">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="b8c05-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="b8c05-128">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b8c05-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8c05-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8c05-129">Remarks</span></span>  
 <span data-ttu-id="b8c05-130">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b8c05-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b8c05-131">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="b8c05-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b8c05-132">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="b8c05-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b8c05-133">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="b8c05-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8c05-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8c05-134">See Also</span></span>  
 <span data-ttu-id="b8c05-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b8c05-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b8c05-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b8c05-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b8c05-137">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b8c05-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b8c05-138">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b8c05-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
