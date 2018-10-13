---
title: '&lt;activityStateQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: a0dae6b90659bd3f53386459513abf92f25b005b
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308310"
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="88030-102">&lt;activityStateQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="88030-102">&lt;activityStateQuery&gt; of WCF</span></span>

<span data-ttu-id="88030-103">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="88030-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="88030-104">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="88030-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="88030-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="88030-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="88030-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="88030-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="88030-107">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="88030-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="88030-108">\<system.serviceModel > \<sledování ></span><span class="sxs-lookup"><span data-stu-id="88030-108">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="88030-109">\<profily > \<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="88030-109">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="88030-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="88030-110">\<workflow></span></span>  
<span data-ttu-id="88030-111">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="88030-111">\<activityStateQueries></span></span>  
<span data-ttu-id="88030-112">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="88030-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88030-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88030-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88030-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="88030-114">Attributes and elements</span></span>  

<span data-ttu-id="88030-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="88030-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88030-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="88030-116">Attributes</span></span>  
  
|<span data-ttu-id="88030-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="88030-117">Attribute</span></span>|<span data-ttu-id="88030-118">Popis</span><span class="sxs-lookup"><span data-stu-id="88030-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88030-119">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="88030-119">activityName</span></span>|<span data-ttu-id="88030-120">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="88030-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88030-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="88030-121">Child elements</span></span>  
  
|<span data-ttu-id="88030-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="88030-122">Element</span></span>|<span data-ttu-id="88030-123">Popis</span><span class="sxs-lookup"><span data-stu-id="88030-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88030-124">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="88030-124">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="88030-125">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="88030-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="88030-126">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="88030-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="88030-127">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="88030-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="88030-128">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="88030-128">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="88030-129">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="88030-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88030-130">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="88030-130">Parent elements</span></span>  
  
|<span data-ttu-id="88030-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="88030-131">Element</span></span>|<span data-ttu-id="88030-132">Popis</span><span class="sxs-lookup"><span data-stu-id="88030-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88030-133">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="88030-133">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="88030-134">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="88030-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="88030-135">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="88030-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88030-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88030-136">Remarks</span></span>

<span data-ttu-id="88030-137">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="88030-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="88030-138">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="88030-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="88030-139">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) prvků, které mají extrahovat všechny proměnné nebo argumentu v jakékoli aktivitě v pracovním postupu. Následující příklad ukazuje k dotazu stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznam je vygenerován.</span><span class="sxs-lookup"><span data-stu-id="88030-139">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="88030-140">Proměnné a argumenty může být extrahována pouze pomocí ActivityStateRecord a tedy přihlášení k odběru v rámci sledovacích profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="88030-140">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88030-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88030-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="88030-142">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="88030-142">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="88030-143">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="88030-143">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
