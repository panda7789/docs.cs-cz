---
title: <activityStateQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 233bd3a2fa161222977902cc1053f964e8171173
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850483"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="a9aa9-102">\<activityStateQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="a9aa9-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="a9aa9-103">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a9aa9-104">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a9aa9-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a9aa9-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="a9aa9-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a9aa9-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="a9aa9-108">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a9aa9-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a9aa9-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a9aa9-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a9aa9-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a9aa9-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a9aa9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="a9aa9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a9aa9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a9aa9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="a9aa9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a9aa9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="a9aa9-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a9aa9-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)</span></span>\
<span data-ttu-id="a9aa9-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQuery >**</span><span class="sxs-lookup"><span data-stu-id="a9aa9-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9aa9-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9aa9-116">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9aa9-117">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a9aa9-117">Attributes and elements</span></span>  

<span data-ttu-id="a9aa9-118">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-118">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9aa9-119">Atributy</span><span class="sxs-lookup"><span data-stu-id="a9aa9-119">Attributes</span></span>  
  
|<span data-ttu-id="a9aa9-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="a9aa9-120">Attribute</span></span>|<span data-ttu-id="a9aa9-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a9aa9-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9aa9-122">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="a9aa9-122">activityName</span></span>|<span data-ttu-id="a9aa9-123">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-123">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9aa9-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a9aa9-124">Child elements</span></span>  
  
|<span data-ttu-id="a9aa9-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9aa9-125">Element</span></span>|<span data-ttu-id="a9aa9-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a9aa9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9aa9-127">\<arguments></span><span class="sxs-lookup"><span data-stu-id="a9aa9-127">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="a9aa9-128">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-128">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="a9aa9-129">\<states></span><span class="sxs-lookup"><span data-stu-id="a9aa9-129">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="a9aa9-130">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-130">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="a9aa9-131">\<states></span><span class="sxs-lookup"><span data-stu-id="a9aa9-131">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="a9aa9-132">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-132">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9aa9-133">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a9aa9-133">Parent elements</span></span>  
  
|<span data-ttu-id="a9aa9-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9aa9-134">Element</span></span>|<span data-ttu-id="a9aa9-135">Popis</span><span class="sxs-lookup"><span data-stu-id="a9aa9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9aa9-136">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="a9aa9-136">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="a9aa9-137">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-137">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a9aa9-138">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-138">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9aa9-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9aa9-139">Remarks</span></span>

<span data-ttu-id="a9aa9-140">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-140">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a9aa9-141">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-141">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a9aa9-142">Můžete použít [ \<argumenty >](../windows-workflow-foundation/arguments.md), [ \<stavy >](../windows-workflow-foundation/states.md) a [ \<>](../windows-workflow-foundation/states.md) prvky pro extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu. Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při vygenerování `Closed` záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-142">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a9aa9-143">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [ \<> ActivityStateQuery](../windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="a9aa9-143">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="a9aa9-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9aa9-144">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="a9aa9-145">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a9aa9-145">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a9aa9-146">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a9aa9-146">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
