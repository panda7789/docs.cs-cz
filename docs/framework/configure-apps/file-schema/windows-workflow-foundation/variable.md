---
title: '&lt;Proměnná&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: c65b377d85783f29ca2a8223e97eb10b073cee0a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155233"
---
# <a name="ltvariablegt"></a><span data-ttu-id="89821-102">&lt;Proměnná&gt;</span><span class="sxs-lookup"><span data-stu-id="89821-102">&lt;variable&gt;</span></span>
<span data-ttu-id="89821-103">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="89821-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="89821-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="89821-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="89821-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="89821-105">\<system.serviceModel></span></span>  
<span data-ttu-id="89821-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="89821-106">\<tracking></span></span>  
<span data-ttu-id="89821-107">\<profily ></span><span class="sxs-lookup"><span data-stu-id="89821-107">\<profiles></span></span>  
<span data-ttu-id="89821-108">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="89821-108">\<trackingProfile></span></span>  
<span data-ttu-id="89821-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="89821-109">\<workflow></span></span>  
<span data-ttu-id="89821-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="89821-110">\<activityStateQueries></span></span>  
<span data-ttu-id="89821-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="89821-111">\<activityStateQuery></span></span>  
<span data-ttu-id="89821-112">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="89821-112">\<variables></span></span>  
<span data-ttu-id="89821-113">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="89821-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89821-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89821-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89821-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="89821-115">Attributes and Elements</span></span>  
 <span data-ttu-id="89821-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="89821-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89821-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="89821-117">Attributes</span></span>  
  
|<span data-ttu-id="89821-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="89821-118">Attribute</span></span>|<span data-ttu-id="89821-119">Popis</span><span class="sxs-lookup"><span data-stu-id="89821-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89821-120">name</span><span class="sxs-lookup"><span data-stu-id="89821-120">name</span></span>|<span data-ttu-id="89821-121">Řetězec, který určuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="89821-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89821-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="89821-122">Child Elements</span></span>  
 <span data-ttu-id="89821-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="89821-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89821-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="89821-124">Parent Elements</span></span>  
  
|<span data-ttu-id="89821-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="89821-125">Element</span></span>|<span data-ttu-id="89821-126">Popis</span><span class="sxs-lookup"><span data-stu-id="89821-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89821-127">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="89821-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="89821-128">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="89821-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89821-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89821-129">Remarks</span></span>  
 <span data-ttu-id="89821-130">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89821-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="89821-131">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="89821-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="89821-132">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="89821-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="89821-133">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="89821-133">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="89821-134">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="89821-134">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89821-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="89821-135">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="89821-136">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="89821-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="89821-137">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="89821-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
