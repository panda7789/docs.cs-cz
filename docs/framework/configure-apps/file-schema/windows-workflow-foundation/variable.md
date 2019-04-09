---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: c85f3c57739c48566c97c8b1debfb7f2c3912bdf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196629"
---
# <a name="variable"></a><span data-ttu-id="8e01a-101">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="8e01a-101">\<variable></span></span>
<span data-ttu-id="8e01a-102">Představuje kolekci proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="8e01a-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="8e01a-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8e01a-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="8e01a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8e01a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8e01a-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="8e01a-105">\<tracking></span></span>  
<span data-ttu-id="8e01a-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="8e01a-106">\<profiles></span></span>  
<span data-ttu-id="8e01a-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8e01a-107">\<trackingProfile></span></span>  
<span data-ttu-id="8e01a-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="8e01a-108">\<workflow></span></span>  
<span data-ttu-id="8e01a-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="8e01a-109">\<activityStateQueries></span></span>  
<span data-ttu-id="8e01a-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="8e01a-110">\<activityStateQuery></span></span>  
<span data-ttu-id="8e01a-111">\<proměnné ></span><span class="sxs-lookup"><span data-stu-id="8e01a-111">\<variables></span></span>  
<span data-ttu-id="8e01a-112">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="8e01a-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e01a-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e01a-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e01a-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8e01a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="8e01a-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8e01a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e01a-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="8e01a-116">Attributes</span></span>  
  
|<span data-ttu-id="8e01a-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="8e01a-117">Attribute</span></span>|<span data-ttu-id="8e01a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8e01a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e01a-119">name</span><span class="sxs-lookup"><span data-stu-id="8e01a-119">name</span></span>|<span data-ttu-id="8e01a-120">Řetězec, který určuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="8e01a-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e01a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8e01a-121">Child Elements</span></span>  
 <span data-ttu-id="8e01a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8e01a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e01a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8e01a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8e01a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e01a-124">Element</span></span>|<span data-ttu-id="8e01a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8e01a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e01a-126">\<Proměnná ></span><span class="sxs-lookup"><span data-stu-id="8e01a-126">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="8e01a-127">Proměnná přidruženého k dotazu stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="8e01a-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e01a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e01a-128">Remarks</span></span>  
 <span data-ttu-id="8e01a-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8e01a-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="8e01a-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="8e01a-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="8e01a-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="8e01a-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="8e01a-132">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="8e01a-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="8e01a-133">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="8e01a-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e01a-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e01a-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8e01a-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8e01a-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8e01a-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8e01a-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
