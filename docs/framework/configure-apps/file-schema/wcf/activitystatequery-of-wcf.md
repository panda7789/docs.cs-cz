---
title: <activityStateQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 49c507424e813067e1dad9b08167d9661acef36f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70991219"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="b6086-102">\<activityStateQuery>služby WCF</span><span class="sxs-lookup"><span data-stu-id="b6086-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="b6086-103">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b6086-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="b6086-104">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b6086-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="b6086-105">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b6086-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="b6086-106">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="b6086-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="b6086-107">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b6086-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="b6086-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6086-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6086-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b6086-109">Attributes and elements</span></span>  

<span data-ttu-id="b6086-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b6086-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6086-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b6086-111">Attributes</span></span>  
  
|<span data-ttu-id="b6086-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b6086-112">Attribute</span></span>|<span data-ttu-id="b6086-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b6086-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6086-114">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="b6086-114">activityName</span></span>|<span data-ttu-id="b6086-115">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="b6086-115">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6086-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b6086-116">Child elements</span></span>  
  
|<span data-ttu-id="b6086-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6086-117">Element</span></span>|<span data-ttu-id="b6086-118">Description</span><span class="sxs-lookup"><span data-stu-id="b6086-118">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="b6086-119">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b6086-119">A collection of arguments associated with this activity query.</span></span>|  
|[\<states>](../windows-workflow-foundation/states.md)|<span data-ttu-id="b6086-120">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="b6086-120">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[\<states>](../windows-workflow-foundation/states.md)|<span data-ttu-id="b6086-121">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="b6086-121">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6086-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="b6086-122">Parent elements</span></span>  
  
|<span data-ttu-id="b6086-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6086-123">Element</span></span>|<span data-ttu-id="b6086-124">Description</span><span class="sxs-lookup"><span data-stu-id="b6086-124">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="b6086-125">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="b6086-125">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b6086-126">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="b6086-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6086-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6086-127">Remarks</span></span>

<span data-ttu-id="b6086-128">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b6086-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b6086-129">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="b6086-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b6086-130">Můžete použít [\<arguments>](../windows-workflow-foundation/arguments.md) [\<states>](../windows-workflow-foundation/states.md) [\<states>](../windows-workflow-foundation/states.md) prvky a k extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b6086-130">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b6086-131">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při `Closed` vygenerování záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="b6086-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b6086-132">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="b6086-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6086-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6086-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="b6086-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b6086-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b6086-135">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b6086-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
