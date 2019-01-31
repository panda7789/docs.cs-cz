---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 9ddb3f1d070531d76201c0b9b5e71f14e2fac496
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257085"
---
# <a name="activitystatequery"></a><span data-ttu-id="ea21c-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ea21c-101">\<activityStateQuery></span></span>
<span data-ttu-id="ea21c-102">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ea21c-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ea21c-103">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ea21c-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ea21c-104">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="ea21c-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ea21c-105">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="ea21c-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="ea21c-106">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ea21c-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ea21c-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ea21c-107">\<system.serviceModel></span></span>  
<span data-ttu-id="ea21c-108">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="ea21c-108">\<tracking></span></span>  
<span data-ttu-id="ea21c-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ea21c-109">\<trackingProfile></span></span>  
<span data-ttu-id="ea21c-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="ea21c-110">\<workflow></span></span>  
<span data-ttu-id="ea21c-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="ea21c-111">\<activityStateQueries></span></span>  
<span data-ttu-id="ea21c-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ea21c-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea21c-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea21c-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea21c-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ea21c-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ea21c-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ea21c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea21c-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="ea21c-116">Attributes</span></span>  
  
|<span data-ttu-id="ea21c-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="ea21c-117">Attribute</span></span>|<span data-ttu-id="ea21c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ea21c-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea21c-119">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="ea21c-119">activityName</span></span>|<span data-ttu-id="ea21c-120">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="ea21c-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea21c-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ea21c-121">Child Elements</span></span>  
  
|<span data-ttu-id="ea21c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="ea21c-122">Element</span></span>|<span data-ttu-id="ea21c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ea21c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea21c-124">\<arguments></span><span class="sxs-lookup"><span data-stu-id="ea21c-124">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="ea21c-125">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="ea21c-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="ea21c-126">\<states></span><span class="sxs-lookup"><span data-stu-id="ea21c-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="ea21c-127">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="ea21c-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="ea21c-128">\<states></span><span class="sxs-lookup"><span data-stu-id="ea21c-128">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="ea21c-129">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="ea21c-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea21c-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ea21c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="ea21c-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="ea21c-131">Element</span></span>|<span data-ttu-id="ea21c-132">Popis</span><span class="sxs-lookup"><span data-stu-id="ea21c-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea21c-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="ea21c-133">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="ea21c-134">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="ea21c-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ea21c-135">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="ea21c-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea21c-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea21c-136">Remarks</span></span>  
 <span data-ttu-id="ea21c-137">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ea21c-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ea21c-138">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="ea21c-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ea21c-139">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="ea21c-139">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ea21c-140">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="ea21c-140">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ea21c-141">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="ea21c-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea21c-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea21c-142">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ea21c-143">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ea21c-143">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ea21c-144">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ea21c-144">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
