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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6621a0f60a6dc916fa1ee34841946929623be88
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="1b598-102">&lt;activityStateQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="1b598-102">&lt;activityStateQuery&gt; of WCF</span></span>
<span data-ttu-id="1b598-103">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1b598-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="1b598-104">Například můžete udržovat přehled o každém dokončení aktivity "Odeslat E-Mail" v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1b598-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="1b598-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="1b598-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="1b598-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="1b598-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="1b598-107">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1b598-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="1b598-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1b598-108">\<system.serviceModel></span></span>  
<span data-ttu-id="1b598-109">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="1b598-109">\<tracking></span></span>  
<span data-ttu-id="1b598-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1b598-110">\<trackingProfile></span></span>  
<span data-ttu-id="1b598-111">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="1b598-111">\<workflow></span></span>  
<span data-ttu-id="1b598-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="1b598-112">\<activityStateQueries></span></span>  
<span data-ttu-id="1b598-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="1b598-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b598-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b598-114">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b598-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1b598-115">Attributes and Elements</span></span>  
 <span data-ttu-id="1b598-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1b598-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b598-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="1b598-117">Attributes</span></span>  
  
|<span data-ttu-id="1b598-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="1b598-118">Attribute</span></span>|<span data-ttu-id="1b598-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1b598-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b598-120">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="1b598-120">activityName</span></span>|<span data-ttu-id="1b598-121">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="1b598-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b598-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1b598-122">Child Elements</span></span>  
  
|<span data-ttu-id="1b598-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b598-123">Element</span></span>|<span data-ttu-id="1b598-124">Popis</span><span class="sxs-lookup"><span data-stu-id="1b598-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b598-125">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="1b598-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="1b598-126">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="1b598-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="1b598-127">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="1b598-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="1b598-128">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="1b598-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="1b598-129">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="1b598-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="1b598-130">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="1b598-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b598-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1b598-131">Parent Elements</span></span>  
  
|<span data-ttu-id="1b598-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b598-132">Element</span></span>|<span data-ttu-id="1b598-133">Popis</span><span class="sxs-lookup"><span data-stu-id="1b598-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b598-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="1b598-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="1b598-135">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="1b598-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1b598-136">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="1b598-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b598-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b598-137">Remarks</span></span>  
 <span data-ttu-id="1b598-138">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1b598-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="1b598-139">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="1b598-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="1b598-140">Můžete použít [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) a [ \<stavy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy extrahujte všechny proměnné nebo argumentu z všechny aktivity v pracovním postupu. Následující příklad ukazuje dotaz stavu aktivity, který extrahuje proměnné a argumenty při aktivity `Closed` sledování záznamu je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="1b598-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="1b598-141">Proměnné a argumenty lze extrahovat jenom s ActivityStateRecord a proto předplacené v rámci sledování profilu pomocí [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="1b598-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b598-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b598-142">See Also</span></span>  
 <span data-ttu-id="1b598-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span><span class="sxs-lookup"><span data-stu-id="1b598-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span></span>    
 <span data-ttu-id="1b598-144"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="1b598-144"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>     
 [<span data-ttu-id="1b598-145">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="1b598-145">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1b598-146">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="1b598-146">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
