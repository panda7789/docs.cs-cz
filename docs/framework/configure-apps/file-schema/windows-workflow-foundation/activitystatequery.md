---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 3c6243e6b8e1d2b32dc830609a5d4df474f48e61
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151168"
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="ee2f5-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="ee2f5-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="ee2f5-103">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ee2f5-104">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ee2f5-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ee2f5-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="ee2f5-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ee2f5-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ee2f5-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ee2f5-108">\<system.serviceModel></span></span>  
<span data-ttu-id="ee2f5-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-109">\<tracking></span></span>  
<span data-ttu-id="ee2f5-110">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-110">\<trackingProfile></span></span>  
<span data-ttu-id="ee2f5-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-111">\<workflow></span></span>  
<span data-ttu-id="ee2f5-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-112">\<activityStateQueries></span></span>  
<span data-ttu-id="ee2f5-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2f5-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee2f5-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee2f5-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ee2f5-115">Attributes and Elements</span></span>  
 <span data-ttu-id="ee2f5-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee2f5-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="ee2f5-117">Attributes</span></span>  
  
|<span data-ttu-id="ee2f5-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="ee2f5-118">Attribute</span></span>|<span data-ttu-id="ee2f5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ee2f5-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee2f5-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="ee2f5-120">activityName</span></span>|<span data-ttu-id="ee2f5-121">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee2f5-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ee2f5-122">Child Elements</span></span>  
  
|<span data-ttu-id="ee2f5-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="ee2f5-123">Element</span></span>|<span data-ttu-id="ee2f5-124">Popis</span><span class="sxs-lookup"><span data-stu-id="ee2f5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee2f5-125">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="ee2f5-126">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="ee2f5-127">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="ee2f5-128">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="ee2f5-129">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="ee2f5-130">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee2f5-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ee2f5-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ee2f5-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="ee2f5-132">Element</span></span>|<span data-ttu-id="ee2f5-133">Popis</span><span class="sxs-lookup"><span data-stu-id="ee2f5-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee2f5-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="ee2f5-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="ee2f5-135">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ee2f5-136">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2f5-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee2f5-137">Remarks</span></span>  
 <span data-ttu-id="ee2f5-138">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ee2f5-139">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ee2f5-140">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ee2f5-141">Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="ee2f5-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ee2f5-142">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="ee2f5-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee2f5-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee2f5-143">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="ee2f5-144">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ee2f5-144">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ee2f5-145">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ee2f5-145">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
