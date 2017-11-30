---
title: "&lt;activityStateQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f1a8639581a4b954609b221038d1e519746178ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="39222-102">&lt;activityStateQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="39222-102">&lt;activityStateQuery&gt; of WCF</span></span>
<span data-ttu-id="39222-103">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="39222-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="39222-104">Například můžete udržovat přehled o každém dokončení aktivity "Odeslat E-Mail" v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="39222-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="39222-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="39222-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="39222-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="39222-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="39222-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="39222-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="39222-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="39222-108">\<system.serviceModel></span></span>  
<span data-ttu-id="39222-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="39222-109">\<tracking></span></span>  
<span data-ttu-id="39222-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="39222-110">\<trackingProfile></span></span>  
<span data-ttu-id="39222-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="39222-111">\<workflow></span></span>  
<span data-ttu-id="39222-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="39222-112">\<activityStateQueries></span></span>  
<span data-ttu-id="39222-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="39222-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39222-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39222-114">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39222-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39222-115">Attributes and Elements</span></span>  
 <span data-ttu-id="39222-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39222-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39222-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="39222-117">Attributes</span></span>  
  
|<span data-ttu-id="39222-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="39222-118">Attribute</span></span>|<span data-ttu-id="39222-119">Popis</span><span class="sxs-lookup"><span data-stu-id="39222-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39222-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="39222-120">activityName</span></span>|<span data-ttu-id="39222-121">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="39222-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39222-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39222-122">Child Elements</span></span>  
  
|<span data-ttu-id="39222-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="39222-123">Element</span></span>|<span data-ttu-id="39222-124">Popis</span><span class="sxs-lookup"><span data-stu-id="39222-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39222-125">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="39222-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="39222-126">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="39222-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="39222-127">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="39222-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="39222-128">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="39222-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="39222-129">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="39222-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="39222-130">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="39222-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39222-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39222-131">Parent Elements</span></span>  
  
|<span data-ttu-id="39222-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="39222-132">Element</span></span>|<span data-ttu-id="39222-133">Popis</span><span class="sxs-lookup"><span data-stu-id="39222-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39222-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="39222-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="39222-135">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="39222-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="39222-136">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="39222-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39222-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39222-137">Remarks</span></span>  
 <span data-ttu-id="39222-138">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="39222-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="39222-139">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="39222-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="39222-140">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="39222-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="39222-141">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="39222-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39222-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="39222-142">See Also</span></span>  
 <span data-ttu-id="39222-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span><span class="sxs-lookup"><span data-stu-id="39222-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span></span>    
 <span data-ttu-id="39222-144"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="39222-144"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>     
 [<span data-ttu-id="39222-145">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="39222-145">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="39222-146">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="39222-146">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
