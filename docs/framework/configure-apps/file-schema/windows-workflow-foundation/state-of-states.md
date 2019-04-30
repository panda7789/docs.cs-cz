---
title: <state> z <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: ff75895949c50cd369e4297ea77dc21106994067
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794405"
---
# <a name="state-of-states"></a><span data-ttu-id="60ff4-102">\<Stav > z \<stavy ></span><span class="sxs-lookup"><span data-stu-id="60ff4-102">\<state> of \<states></span></span>
<span data-ttu-id="60ff4-103">Konfigurace element, který obsahuje informace o stavu předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="60ff4-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="60ff4-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="60ff4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="60ff4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="60ff4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="60ff4-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="60ff4-106">\<tracking></span></span>  
<span data-ttu-id="60ff4-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="60ff4-107">\<trackingProfile></span></span>  
<span data-ttu-id="60ff4-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="60ff4-108">\<workflow></span></span>  
<span data-ttu-id="60ff4-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="60ff4-109">\<activityStateQueries></span></span>  
<span data-ttu-id="60ff4-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="60ff4-110">\<activityStateQuery></span></span>  
<span data-ttu-id="60ff4-111">\<states></span><span class="sxs-lookup"><span data-stu-id="60ff4-111">\<states></span></span>  
<span data-ttu-id="60ff4-112">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="60ff4-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ff4-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60ff4-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60ff4-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60ff4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="60ff4-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60ff4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60ff4-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="60ff4-116">Attributes</span></span>  
  
|<span data-ttu-id="60ff4-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="60ff4-117">Attribute</span></span>|<span data-ttu-id="60ff4-118">Popis</span><span class="sxs-lookup"><span data-stu-id="60ff4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60ff4-119">name</span><span class="sxs-lookup"><span data-stu-id="60ff4-119">name</span></span>|<span data-ttu-id="60ff4-120">Řetězec, který určuje stav předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="60ff4-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60ff4-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60ff4-121">Child Elements</span></span>  
 <span data-ttu-id="60ff4-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="60ff4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60ff4-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60ff4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="60ff4-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="60ff4-124">Element</span></span>|<span data-ttu-id="60ff4-125">Popis</span><span class="sxs-lookup"><span data-stu-id="60ff4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ff4-126">\<states></span><span class="sxs-lookup"><span data-stu-id="60ff4-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="60ff4-127">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="60ff4-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60ff4-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60ff4-128">Remarks</span></span>  
 <span data-ttu-id="60ff4-129">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="60ff4-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="60ff4-130">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="60ff4-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="60ff4-131">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="60ff4-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="60ff4-132">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="60ff4-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="60ff4-133">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="60ff4-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60ff4-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60ff4-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="60ff4-135">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="60ff4-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="60ff4-136">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="60ff4-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
