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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51476e9d3fc0e57ec261f63683dc139491541bce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltvariablesgt"></a><span data-ttu-id="9af05-102">&lt;proměnné&gt;</span><span class="sxs-lookup"><span data-stu-id="9af05-102">&lt;variables&gt;</span></span>
<span data-ttu-id="9af05-103">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="9af05-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="9af05-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9af05-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9af05-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9af05-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9af05-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9af05-106">\<tracking></span></span>  
<span data-ttu-id="9af05-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9af05-107">\<trackingProfile></span></span>  
<span data-ttu-id="9af05-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9af05-108">\<workflow></span></span>  
<span data-ttu-id="9af05-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="9af05-109">\<activityStateQueries></span></span>  
<span data-ttu-id="9af05-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="9af05-110">\<activityStateQuery></span></span>  
<span data-ttu-id="9af05-111">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="9af05-111">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af05-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9af05-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9af05-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9af05-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9af05-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9af05-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9af05-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="9af05-115">Attributes</span></span>  
 <span data-ttu-id="9af05-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="9af05-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9af05-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9af05-117">Child Elements</span></span>  
  
|<span data-ttu-id="9af05-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="9af05-118">Element</span></span>|<span data-ttu-id="9af05-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9af05-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9af05-120">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="9af05-120">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="9af05-121">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="9af05-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9af05-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9af05-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9af05-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="9af05-123">Element</span></span>|<span data-ttu-id="9af05-124">Popis</span><span class="sxs-lookup"><span data-stu-id="9af05-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9af05-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="9af05-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="9af05-126">Představuje konfiguraci elementu, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="9af05-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="9af05-127">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="9af05-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9af05-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9af05-128">Remarks</span></span>  
 <span data-ttu-id="9af05-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9af05-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="9af05-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="9af05-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="9af05-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="9af05-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="9af05-132">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="9af05-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9af05-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="9af05-133">See Also</span></span>  
 <span data-ttu-id="9af05-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9af05-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9af05-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9af05-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="9af05-136">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="9af05-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9af05-137">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="9af05-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
