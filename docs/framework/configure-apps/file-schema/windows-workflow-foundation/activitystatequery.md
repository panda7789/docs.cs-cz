---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 5d3c35589330ab5bed5f89c0dafac006b9e3af55
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398942"
---
# \<activityStateQuery>
<span data-ttu-id="7f183-101">Představuje dotaz, který se používá ke sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7f183-101">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="7f183-102">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7f183-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="7f183-103">Tento dotaz je nezbytné pro sledování účastníka přihlásit k odběru objekty záznam stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7f183-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="7f183-104">Dostupné stavy přihlásit k odběru jsou uvedeny v ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="7f183-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="7f183-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7f183-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="7f183-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f183-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f183-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f183-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7f183-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f183-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f183-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f183-109">Attributes</span></span>  
  
|<span data-ttu-id="7f183-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f183-110">Attribute</span></span>|<span data-ttu-id="7f183-111">Popis</span><span class="sxs-lookup"><span data-stu-id="7f183-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f183-112">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="7f183-112">activityName</span></span>|<span data-ttu-id="7f183-113">Řetězec, který určuje název aktivity k filtrování <xref:System.Activities.Tracking.ActivityStateRecord> instancí na.</span><span class="sxs-lookup"><span data-stu-id="7f183-113">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f183-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f183-114">Child Elements</span></span>  
  
|<span data-ttu-id="7f183-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f183-115">Element</span></span>|<span data-ttu-id="7f183-116">Description</span><span class="sxs-lookup"><span data-stu-id="7f183-116">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="7f183-117">Kolekce argumenty přidružené k tomuto dotazu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7f183-117">A collection of arguments associated with this activity query.</span></span>|  
|[\<states>](states.md)|<span data-ttu-id="7f183-118">Kolekce elementů konfigurace, které obsahují stavy předplacenému aktivity, pro který by měl vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="7f183-118">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[\<states>](states.md)|<span data-ttu-id="7f183-119">Kolekce proměnných spojených s Tento dotaz aktivity.</span><span class="sxs-lookup"><span data-stu-id="7f183-119">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f183-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f183-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7f183-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f183-121">Element</span></span>|<span data-ttu-id="7f183-122">Description</span><span class="sxs-lookup"><span data-stu-id="7f183-122">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="7f183-123">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="7f183-123">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7f183-124">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="7f183-124">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f183-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f183-125">Remarks</span></span>  
 <span data-ttu-id="7f183-126">Jeden jedinečné funkce ActivityStateQuery je schopnost extrahování dat při sledování provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7f183-126">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="7f183-127">Tímto způsobem další kontext při přístupu k sledování záznamů příspěvek provádění.</span><span class="sxs-lookup"><span data-stu-id="7f183-127">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="7f183-128">Můžete použít [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) prvky a k extrakci jakékoli proměnné nebo argumentu z jakékoli aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="7f183-128">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="7f183-129">Následující příklad ukazuje dotaz na stav aktivity, který extrahuje proměnné a argumenty při `Closed` vygenerování záznamu sledování aktivity.</span><span class="sxs-lookup"><span data-stu-id="7f183-129">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="7f183-130">Proměnné a argumenty lze extrahovat pouze pomocí ActivityStateRecord, a proto jsou přihlášeni v rámci sledovacího profilu pomocí [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="7f183-130">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f183-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f183-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7f183-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7f183-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7f183-133">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="7f183-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
