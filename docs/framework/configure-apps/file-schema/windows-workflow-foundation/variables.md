---
title: "&lt;proměnné&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c3eee12b8212243f286bb21604904b37273921e6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltvariablesgt"></a><span data-ttu-id="e34c5-102">&lt;proměnné&gt;</span><span class="sxs-lookup"><span data-stu-id="e34c5-102">&lt;variables&gt;</span></span>
<span data-ttu-id="e34c5-103">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="e34c5-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="e34c5-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e34c5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e34c5-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e34c5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e34c5-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e34c5-106">\<tracking></span></span>  
<span data-ttu-id="e34c5-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e34c5-107">\<trackingProfile></span></span>  
<span data-ttu-id="e34c5-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="e34c5-108">\<workflow></span></span>  
<span data-ttu-id="e34c5-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="e34c5-109">\<activityStateQueries></span></span>  
<span data-ttu-id="e34c5-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e34c5-110">\<activityStateQuery></span></span>  
<span data-ttu-id="e34c5-111">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="e34c5-111">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34c5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e34c5-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e34c5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e34c5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e34c5-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e34c5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e34c5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="e34c5-115">Attributes</span></span>  
 <span data-ttu-id="e34c5-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e34c5-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e34c5-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e34c5-117">Child Elements</span></span>  
  
|<span data-ttu-id="e34c5-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e34c5-118">Element</span></span>|<span data-ttu-id="e34c5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e34c5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e34c5-120">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="e34c5-120">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="e34c5-121">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="e34c5-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e34c5-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e34c5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e34c5-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="e34c5-123">Element</span></span>|<span data-ttu-id="e34c5-124">Popis</span><span class="sxs-lookup"><span data-stu-id="e34c5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e34c5-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e34c5-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="e34c5-126">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="e34c5-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e34c5-127">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="e34c5-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e34c5-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e34c5-128">Remarks</span></span>  
 <span data-ttu-id="e34c5-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e34c5-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e34c5-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="e34c5-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e34c5-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="e34c5-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e34c5-132">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="e34c5-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e34c5-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="e34c5-133">See Also</span></span>  
 <span data-ttu-id="e34c5-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e34c5-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e34c5-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e34c5-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e34c5-136">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="e34c5-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e34c5-137">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="e34c5-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
