---
title: '&lt;Proměnná&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 7d41d80bfe83cfafca01509d50709e21730bcb97
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltvariablegt"></a><span data-ttu-id="dea6e-102">&lt;Proměnná&gt;</span><span class="sxs-lookup"><span data-stu-id="dea6e-102">&lt;variable&gt;</span></span>
<span data-ttu-id="dea6e-103">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="dea6e-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="dea6e-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dea6e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="dea6e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dea6e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="dea6e-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="dea6e-106">\<tracking></span></span>  
<span data-ttu-id="dea6e-107">\<profily ></span><span class="sxs-lookup"><span data-stu-id="dea6e-107">\<profiles></span></span>  
<span data-ttu-id="dea6e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="dea6e-108">\<trackingProfile></span></span>  
<span data-ttu-id="dea6e-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="dea6e-109">\<workflow></span></span>  
<span data-ttu-id="dea6e-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="dea6e-110">\<activityStateQueries></span></span>  
<span data-ttu-id="dea6e-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="dea6e-111">\<activityStateQuery></span></span>  
<span data-ttu-id="dea6e-112">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="dea6e-112">\<variables></span></span>  
<span data-ttu-id="dea6e-113">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="dea6e-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea6e-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dea6e-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dea6e-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dea6e-115">Attributes and Elements</span></span>  
 <span data-ttu-id="dea6e-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dea6e-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dea6e-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="dea6e-117">Attributes</span></span>  
  
|<span data-ttu-id="dea6e-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="dea6e-118">Attribute</span></span>|<span data-ttu-id="dea6e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="dea6e-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dea6e-120">name</span><span class="sxs-lookup"><span data-stu-id="dea6e-120">name</span></span>|<span data-ttu-id="dea6e-121">Řetězec, který určuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="dea6e-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dea6e-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dea6e-122">Child Elements</span></span>  
 <span data-ttu-id="dea6e-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="dea6e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dea6e-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dea6e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dea6e-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="dea6e-125">Element</span></span>|<span data-ttu-id="dea6e-126">Popis</span><span class="sxs-lookup"><span data-stu-id="dea6e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dea6e-127">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="dea6e-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="dea6e-128">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="dea6e-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dea6e-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dea6e-129">Remarks</span></span>  
 <span data-ttu-id="dea6e-130">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dea6e-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="dea6e-131">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="dea6e-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="dea6e-132">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="dea6e-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="dea6e-133">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="dea6e-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dea6e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="dea6e-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="dea6e-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="dea6e-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="dea6e-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="dea6e-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
